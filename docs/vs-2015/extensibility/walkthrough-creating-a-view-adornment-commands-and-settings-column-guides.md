---
title: 'Procédure pas à pas : création d’un ornement, de commandes et de paramètres View (repères de colonne) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 4a2df0a3-42da-4f7b-996f-ee16a35ac922
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0cab24a373595ca1257cbdaa50c009eefa713ea7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148839"
---
# <a name="walkthrough-creating-a-view-adornment-commands-and-settings-column-guides"></a>Procédure pas à pas : création d’un ornement, de commandes et de paramètres pour l’affichage (repères de colonne)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez étendre l’éditeur de texte/Code de Visual Studio avec des commandes et des effets de vue. Cette rubrique vous montre comment prendre en main une fonctionnalité d’extension populaire, repères de colonne. Les repères de colonne sont des lignes visuelles qui s’affichent dans la vue de l’éditeur de texte pour vous aider à gérer votre code à des largeurs de colonne spécifiques. Le code spécifiquement mis en forme peut être important pour les exemples que vous incluez dans des documents, des billets de blog ou des rapports de bogues.

Lors de cette procédure pas à pas, vous allez :

- Créer un projet VSIX
- Ajouter un ornement de vue de l’éditeur
- Ajouter la prise en charge de l’enregistrement et de l’obtention des paramètres (où vous pouvez dessiner des repères de colonne et leur couleur)
- Ajouter des commandes (ajouter/supprimer des repères de colonne, modifier leur couleur)
- Placez les commandes dans les menus contextuels du menu Edition et du document texte
- Ajouter la prise en charge de l’appel des commandes à partir de la fenêtre commande de Visual Studio  
  
  Vous pouvez essayer une version de la fonctionnalité repères de colonne avec cette[extension](https://visualstudiogallery.msdn.microsoft.com/da227a0b-0e31-4a11-8f6b-3a149cf2e459?SRC=Home)de la Galerie Visual Studio.  
  
  **Remarque**: dans cette procédure pas à pas, vous collez un grand nombre de code dans quelques fichiers générés par les modèles d’extension Visual Studio, mais cette procédure pas à pas fera bientôt référence à une solution terminée sur GitHub avec d’autres exemples d’extensions. Le code complet est légèrement différent en ce qu’il contient des icônes de commandes réelles au lieu d’utiliser des icônes generictemplate.

## <a name="getting-started"></a>Mise en route
À compter de Visual Studio 2015, vous n’installez pas le kit de développement logiciel (SDK) Visual Studio à partir du centre de téléchargement. Il est inclus en tant que fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit de développement logiciel (SDK) Visual Studio plus tard. Pour plus d’informations, consultez [installation du kit de développement logiciel (SDK) Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="setting-up-the-solution"></a>Configuration de la solution
Tout d’abord, vous allez créer un projet VSIX, ajouter un ornement de vue de l’éditeur, puis ajouter une commande (qui ajoute un VSPackage pour être propriétaire de la commande). L’architecture de base est la suivante :

- Vous disposez d’un écouteur de création de vue de texte qui crée un `ColumnGuideAdornment` objet par vue. Cet objet écoute les événements relatifs aux repères de colonne modification ou modification des paramètres, mise à jour ou redessination, si nécessaire.
- Il y a un `GuidesSettingsManager` qui gère la lecture et l’écriture à partir du stockage des paramètres de Visual Studio. Le gestionnaire de paramètres comporte également des opérations de mise à jour des paramètres qui prennent en charge les commandes utilisateur (ajouter une colonne, supprimer une colonne, modifier la couleur).
- Un package VSIP est nécessaire si vous avez des commandes utilisateur, mais il s’agit simplement d’un code réutilisable qui initialise l’objet d’implémentation de commandes.
- Il existe un `ColumnGuideCommands` objet qui implémente les commandes utilisateur et raccorde les gestionnaires de commandes pour les commandes déclarées dans le fichier. vsct.
  
  **VSIX**. Utiliser le **fichier &#124; nouveau...** pour créer un projet. Choisissez le nœud extensibilité sous C# dans le volet de navigation gauche, puis choisissez **projet VSIX** dans le volet droit. Entrez le nom ColumnGuides, puis choisissez **OK** pour créer le projet.
  
  **Afficher l’ornement**. Appuyez sur le bouton de pointeur droit sur le nœud du projet dans la Explorateur de solutions. Choisissez **ajouter &#124; nouvel élément...** pour ajouter un nouvel élément d’ornement de vue. Choisissez **extensibilité &#124; Editor** dans le volet de navigation gauche, puis choisissez l’ornement de la **fenêtre d’affichage** de l’éditeur dans le volet droit. Entrez le nom ColumnGuideAdornment comme nom d’élément, puis choisissez **Ajouter** pour l’ajouter.
  
  Vous pouvez voir que ce modèle d’élément a ajouté deux fichiers au projet (ainsi que des références, etc.) : ColumnGuideAdornment.cs et ColumnGuideAdornmentTextViewCreationListener.cs. Les modèles dessinent simplement un rectangle violet sur la vue. Ci-dessous, vous allez modifier deux lignes dans l’écouteur de création de vue et remplacer le contenu de ColumnGuideAdornment.cs.
  
  **Commandes**. Appuyez sur le bouton de pointeur droit sur le nœud du projet dans la Explorateur de solutions. Choisissez **ajouter &#124; nouvel élément...** pour ajouter un nouvel élément d’ornement de vue. Choisissez **extensibilité &#124; VSPackage** dans le volet de navigation gauche et choisissez **commande personnalisée** dans le volet droit. Entrez le nom ColumnGuideCommands comme nom d’élément, puis choisissez **Ajouter** pour l’ajouter. En plus de plusieurs références, l’ajout des commandes et du package a ajouté ColumnGuideCommands.cs, ColumnGuideCommandsPackage.cs et ColumnGuideCommandsPackage. vsct. Ci-dessous, vous allez remplacer le contenu des premier et dernier fichiers pour définir et implémenter les commandes.

## <a name="setting-up-the-text-view-creation-listener"></a>Configuration de l’écouteur de création d’un affichage de texte
Ouvrez ColumnGuideAdornmentTextViewCreationListener.cs dans l’éditeur. Ce code implémente un gestionnaire pour chaque fois que Visual Studio crée des affichages de texte. Des attributs contrôlent le moment où le gestionnaire est appelé, selon les caractéristiques de la vue.

Le code doit également déclarer une couche d’ornement. Lorsque l’éditeur met à jour des vues, il obtient les couches d’ornement pour la vue et de qui obtient les éléments d’ornement. Vous pouvez déclarer le classement de votre couche par rapport aux autres avec des attributs. Remplacez la ligne suivante :

```csharp
[Order(After = PredefinedAdornmentLayers.Caret)]
```

 avec ces deux lignes :

```csharp
[Order(Before = PredefinedAdornmentLayers.Text)]
[TextViewRole(PredefinedTextViewRoles.Document)]
```

La ligne que vous avez remplacée se trouve dans un groupe d’attributs qui déclarent une couche d’ornement.  La première ligne vous avez modifié uniquement les modifications où les lignes de repère de colonne apparaissent. Le fait de dessiner les lignes avant le texte de la vue signifie qu’elles apparaissent derrière le texte ou en dessous. La deuxième ligne déclare que les ornements du repère de colonne s’appliquent aux entités de texte qui correspondent à votre notion de document, mais vous pouvez déclarer l’ornement, par exemple, pour travailler uniquement pour du texte modifiable. Il y a plus d’informations sur [les points d’extension du service de langage et](../extensibility/language-service-and-editor-extension-points.md) de l’éditeur

## <a name="implementing-the-settings-manager"></a>Implémentation du gestionnaire de paramètres
Remplacez le contenu de GuidesSettingsManager.cs par le code suivant (décrit ci-dessous) :

```csharp
using Microsoft.VisualStudio.Settings;
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.Shell.Settings;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Windows.Media;

namespace ColumnGuides
{
    internal static class GuidesSettingsManager
    {
        // Because my code is always called from the UI thred, this succeeds.
        internal static SettingsManager VsManagedSettingsManager =
            new ShellSettingsManager(ServiceProvider.GlobalProvider);

        private const int _maxGuides = 5;
        private const string _collectionSettingsName = "Text Editor";
        private const string _settingName = "Guides";
        // 1000 seems reasonable since primary scenario is long lines of code
        private const int _maxColumn = 1000;

        static internal bool AddGuideline(int column)
        {
            if (! IsValidColumn(column))
                throw new ArgumentOutOfRangeException(
                    "column",
                    "The paramenter must be between 1 and " + _maxGuides.ToString());
            var offsets = GuidesSettingsManager.GetColumnOffsets();
            if (offsets.Count() >= _maxGuides)
                return false;
            // Check for duplicates
            if (offsets.Contains(column))
                return false;
            offsets.Add(column);
            WriteSettings(GuidesSettingsManager.GuidelinesColor, offsets);
            return true;
        }

        static internal bool RemoveGuideline(int column)
        {
            if (!IsValidColumn(column))
                throw new ArgumentOutOfRangeException(
                    "column", "The paramenter must be between 1 and 10,000");
            var columns = GuidesSettingsManager.GetColumnOffsets();
            if (! columns.Remove(column))
            {
                // Not present. Allow user to remove the last column 
                // even if they're not on the right column.
                if (columns.Count != 1)
                    return false;

                columns.Clear();
            }
            WriteSettings(GuidesSettingsManager.GuidelinesColor, columns);
            return true;
        }

        static internal bool CanAddGuideline(int column)
        {
            if (!IsValidColumn(column))
                return false;
            var offsets = GetColumnOffsets();
            if (offsets.Count >= _maxGuides)
                return false;
            return ! offsets.Contains(column);
        }

        static internal bool CanRemoveGuideline(int column)
        {
            if (! IsValidColumn(column))
                return false;
            // Allow user to remove the last guideline regardless of the column.
            // Okay to call count, we limit the number of guides.
            var offsets = GuidesSettingsManager.GetColumnOffsets();
            return offsets.Contains(column) || offsets.Count() == 1;
        }

        static internal void RemoveAllGuidelines()
        {
            WriteSettings(GuidesSettingsManager.GuidelinesColor, new int[0]);
        }

        private static bool IsValidColumn(int column)
        {
            // zero is allowed (per user request)
            return 0 <= column && column <= _maxColumn;
        }

        // This has format "RGB(<int>, <int>, <int>) <int> <int>...".
        // There can be any number of ints following the RGB part,
        // and each int is a column (char offset into line) where to draw.
        static private string _guidelinesConfiguration;
        static private string GuidelinesConfiguration
        {
            get
            {
                if (_guidelinesConfiguration == null)
                {
                    _guidelinesConfiguration =
                        GetUserSettingsString(
                            GuidesSettingsManager._collectionSettingsName,
                            GuidesSettingsManager._settingName)
                        .Trim();
                }
                return _guidelinesConfiguration;
            }

            set
            {
                if (value != _guidelinesConfiguration)
                {
                    _guidelinesConfiguration = value;
                    WriteUserSettingsString(
                        GuidesSettingsManager._collectionSettingsName,
                        GuidesSettingsManager._settingName, value);
                    // Notify ColumnGuideAdornments to update adornments in views.
                    var handler = GuidesSettingsManager.SettingsChanged;
                    if (handler != null)
                        handler();
                }
            }
        }

        internal static string GetUserSettingsString(string collection, string setting)
        {
            var store = GuidesSettingsManager
                            .VsManagedSettingsManager
                            .GetReadOnlySettingsStore(SettingsScope.UserSettings);
            return store.GetString(collection, setting, "RGB(255,0,0) 80");
        }

        internal static void WriteUserSettingsString(string key, string propertyName,
                                                     string value)
        {
            var store = GuidesSettingsManager
                            .VsManagedSettingsManager
                            .GetWritableSettingsStore(SettingsScope.UserSettings);
            store.CreateCollection(key);
            store.SetString(key, propertyName, value);
        }

        // Persists settings and sets property with side effect of signaling
        // ColumnGuideAdornments to update.
        static private void WriteSettings(Color color, IEnumerable<int> columns)
        {
            string value = ComposeSettingsString(color, columns);
            GuidelinesConfiguration = value;
        }

        private static string ComposeSettingsString(Color color,
                                                    IEnumerable<int> columns)
        {
            StringBuilder sb = new StringBuilder();
            sb.AppendFormat("RGB({0},{1},{2})", color.R, color.G, color.B);
            IEnumerator<int> columnsEnumerator = columns.GetEnumerator();
            if (columnsEnumerator.MoveNext())
            {
                sb.AppendFormat(" {0}", columnsEnumerator.Current);
                while (columnsEnumerator.MoveNext())
                {
                    sb.AppendFormat(", {0}", columnsEnumerator.Current);
                }
            }
            return sb.ToString();
        }

        // Parse a color out of a string that begins like "RGB(255,0,0)"
        static internal Color GuidelinesColor
        {
            get
            {
                string config = GuidelinesConfiguration;
                if (!String.IsNullOrEmpty(config) && config.StartsWith("RGB("))
                {
                    int lastParen = config.IndexOf(')');
                    if (lastParen > 4)
                    {
                        string[] rgbs = config.Substring(4, lastParen - 4).Split(',');

                        if (rgbs.Length >= 3)
                        {
                            byte r, g, b;
                            if (byte.TryParse(rgbs[0], out r) &&
                                byte.TryParse(rgbs[1], out g) &&
                                byte.TryParse(rgbs[2], out b))
                            {
                                return Color.FromRgb(r, g, b);
                            }
                        }
                    }
                }
                return Colors.DarkRed;
            }

            set
            {
                WriteSettings(value, GetColumnOffsets());
            }
        }

        // Parse a list of integer values out of a string that looks like
        // "RGB(255,0,0) 1, 5, 10, 80"
        static internal List<int> GetColumnOffsets()
        {
            var result = new List<int>();
            string settings = GuidesSettingsManager.GuidelinesConfiguration;
            if (String.IsNullOrEmpty(settings))
                return new List<int>();

            if (!settings.StartsWith("RGB("))
                return new List<int>();

            int lastParen = settings.IndexOf(')');
            if (lastParen <= 4)
                return new List<int>();

            string[] columns = settings.Substring(lastParen + 1).Split(',');

            int columnCount = 0;
            foreach (string columnText in columns)
            {
                int column = -1;
                // VS 2008 gallery extension didn't allow zero, so per user request ...
                if (int.TryParse(columnText, out column) && column >= 0)
                {
                    columnCount++;
                    result.Add(column);
                    if (columnCount >= _maxGuides)
                        break;
                }
            }
            return result;
        }

        // Delegate and Event to fire when settings change so that ColumnGuideAdornments
        // can update. We need nothing special in this event since the settings manager
        // is statically available.
        //
        internal delegate void SettingsChangedHandler();
        static internal event SettingsChangedHandler SettingsChanged;

    }
}

```

La majeure partie de ce code crée et analyse simplement le format des paramètres : « RGB ( \<int> , \<int> , \<int> ) \<int> , \<int> ,... ». Les entiers à la fin sont les colonnes de base 1 où vous souhaitez insérer des repères de colonne. L’extension repères de colonne capture tous ses paramètres dans une chaîne de valeur de paramètre unique.

Certaines parties du code méritent une mise en évidence. La ligne de code suivante obtient le wrapper managé Visual Studio pour le stockage des paramètres. Pour l’essentiel, cela se résume au registre Windows, mais cette API est indépendante du mécanisme de stockage.

```csharp
internal static SettingsManager VsManagedSettingsManager =
    new ShellSettingsManager(ServiceProvider.GlobalProvider);
```

 Le stockage des paramètres de Visual Studio utilise un identificateur de catégorie et un identificateur de paramètre pour identifier de manière unique tous les paramètres :

```csharp
private const string _collectionSettingsName = "Text Editor";
private const string _settingName = "Guides";
```

Vous n’avez pas besoin d’utiliser `“Text Editor”` comme nom de catégorie et vous pouvez choisir tout ce que vous aimez.

Les premières fonctions sont les points d’entrée pour modifier les paramètres. Ils vérifient les contraintes de haut niveau, comme le nombre maximal de guides autorisés. Ensuite, ils appellent `WriteSettings` qui composent une chaîne de paramètres et définit la propriété `GuideLinesConfiguration` . La définition de cette propriété enregistre la valeur des paramètres dans le magasin de paramètres de Visual Studio et déclenche l' `SettingsChanged` événement pour mettre à jour tous les `ColumnGuideAdornment` objets associés à un affichage de texte.

Il existe deux fonctions de point d’entrée, telles que `CanAddGuideline` , qui sont utilisées pour implémenter les commandes qui modifient les paramètres. Lorsque Visual Studio affiche des menus, il interroge les implémentations de commande pour déterminer si la commande est actuellement activée, son nom, etc. Vous verrez ci-dessous comment raccorder ces points d’entrée pour les implémentations de commande. Pour plus d’informations sur les commandes [, consultez extension des menus et des commandes](../extensibility/extending-menus-and-commands.md) .

## <a name="implementing-the-columnguideadornment-class"></a>Implémentation de la classe ColumnGuideAdornment
La `ColumnGuideAdornment` classe est instanciée pour chaque vue de texte qui peut avoir des ornements. Cette classe écoute les événements relatifs aux repères de colonne modification ou modification des paramètres, mise à jour ou redessination, si nécessaire.

Remplacez le contenu de ColumnGuideAdornment.cs par le code suivant (décrit ci-dessous) :

```csharp
using System;
using System.Windows.Media;
using Microsoft.VisualStudio.Text.Editor;
using System.Collections.Generic;
using System.Windows.Shapes;
using Microsoft.VisualStudio.Text.Formatting;
using System.Windows;

namespace ColumnGuides
{
    /// <summary>
    /// Adornment class, one instance per text view that draws a guides on the viewport
    /// </summary>
    internal sealed class ColumnGuideAdornment
    {
        private const double _lineThickness = 1.0;
        private IList<Line> _guidelines;
        private IWpfTextView _view;
        private double _baseIndentation;
        private double _columnWidth;

        /// <summary>
        /// Creates editor column guidelines
        /// </summary>
        /// <param name="view">The <see cref="IWpfTextView"/> upon
        /// which the adornment will be drawn</param>
        public ColumnGuideAdornment(IWpfTextView view)
        {
            _view = view;
            _guidelines = CreateGuidelines();
            GuidesSettingsManager.SettingsChanged +=
                new GuidesSettingsManager.SettingsChangedHandler(SettingsChanged);
            view.LayoutChanged +=
                new EventHandler<TextViewLayoutChangedEventArgs>(OnViewLayoutChanged);
            _view.Closed += new EventHandler(OnViewClosed);
        }

        void SettingsChanged()
        {
            _guidelines = CreateGuidelines();
            UpdatePositions();
            AddGuidelinesToAdornmentLayer();
        }

        void OnViewClosed(object sender, EventArgs e)
        {
            _view.LayoutChanged -= OnViewLayoutChanged;
            _view.Closed -= OnViewClosed;
            GuidesSettingsManager.SettingsChanged -= SettingsChanged;
        }

        private bool _firstLayoutDone;

        void OnViewLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)
        {
            bool fUpdatePositions = false;

            IFormattedLineSource lineSource = _view.FormattedLineSource;
            if (lineSource == null)
            {
                return;
            }
            if (_columnWidth != lineSource.ColumnWidth)
            {
                _columnWidth = lineSource.ColumnWidth;
                fUpdatePositions = true;
            }
            if (_baseIndentation != lineSource.BaseIndentation)
            {
                _baseIndentation = lineSource.BaseIndentation;
                fUpdatePositions = true;
            }
            if (fUpdatePositions ||
                e.VerticalTranslation ||
                e.NewViewState.ViewportTop != e.OldViewState.ViewportTop ||
                e.NewViewState.ViewportBottom != e.OldViewState.ViewportBottom)
            {
                UpdatePositions();
            }
            if (!_firstLayoutDone)
            {
                AddGuidelinesToAdornmentLayer();
                _firstLayoutDone = true;
            }
        }

        private static IList<Line> CreateGuidelines()
        {
            Brush lineBrush = new SolidColorBrush(GuidesSettingsManager.GuidelinesColor);
            DoubleCollection dashArray = new DoubleCollection(new double[] { 1.0, 3.0 });
            IList<Line> result = new List<Line>();
            foreach (int column in GuidesSettingsManager.GetColumnOffsets())
            {
                Line line = new Line()
                {
                    // Use the DataContext slot as a cookie to hold the column
                    DataContext = column,
                    Stroke = lineBrush,
                    StrokeThickness = _lineThickness,
                    StrokeDashArray = dashArray
                };
                result.Add(line);
            }
            return result;
        }

        void UpdatePositions()
        {
            foreach (Line line in _guidelines)
            {
                int column = (int)line.DataContext;
                line.X2 = _baseIndentation + 0.5 + column * _columnWidth;
                line.X1 = line.X2;
                line.Y1 = _view.ViewportTop;
                line.Y2 = _view.ViewportBottom;
            }
        }

        void AddGuidelinesToAdornmentLayer()
        {
            // Grab a reference to the adornment layer that this adornment
            // should be added to
            // Must match exported name in ColumnGuideAdornmentTextViewCreationListener
            IAdornmentLayer adornmentLayer =
                _view.GetAdornmentLayer("ColumnGuideAdornment");
            if (adornmentLayer == null)
                return;
            adornmentLayer.RemoveAllAdornments();
            // Add the guidelines to the adornment layer and make them relative
            // to the viewport
            foreach (UIElement element in _guidelines)
                adornmentLayer.AddAdornment(AdornmentPositioningBehavior.OwnerControlled,
                                            null, null, element, null);
        }
    }

}
```

Les instances de cette classe contiennent le associé <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> et une liste d' `Line` objets dessinés sur la vue.

Le constructeur (appelé à partir de `ColumnGuideAdornmentTextViewCreationListener` Lorsque Visual Studio crée des vues) crée les objets de repère de colonne `Line` . Le constructeur ajoute également des gestionnaires pour l' `SettingsChanged` événement (défini dans `GuidesSettingsManager` ) et les événements d’affichage `LayoutChanged` et `Closed` .

L' `LayoutChanged` événement se déclenche en raison de plusieurs types de modifications dans la vue, y compris lorsque Visual Studio crée la vue. Le `OnViewLayoutChanged` Gestionnaire appelle `AddGuidelinesToAdornmentLayer` pour exécuter. Le code dans `OnViewLayoutChanged` détermine s’il doit mettre à jour les positions des lignes en fonction des modifications telles que les modifications de la taille de la police, afficher les gouttières, le défilement horizontal, etc. Le code dans `UpdatePositions` provoque le dessin des lignes de repère entre les caractères ou juste après la colonne de texte qui se trouve dans l’offset de caractère spécifié dans la ligne de texte.

Chaque fois que des paramètres modifient la `SettingsChanged` fonction, il suffit de recréer tous les `Line` objets avec les nouveaux paramètres. Après avoir défini les positions de ligne, le code supprime tous les `Line` objets précédents de la `ColumnGuideAdornment` couche d’ornement et en ajoute les nouveaux.

## <a name="defining-the-commands-menus-and-menu-placements"></a>Définition des commandes, menus et placements de menus
Il peut être important de déclarer des commandes et des menus, de placer des groupes de commandes ou de menus dans d’autres menus et de raccorder des gestionnaires de commandes. Cette procédure pas à pas explique comment les commandes fonctionnent dans cette extension, mais pour plus d’informations, consultez [extension des menus et des commandes](../extensibility/extending-menus-and-commands.md).

### <a name="introduction-to-the-code"></a>Présentation du code
L’extension repères de colonne illustre la déclaration d’un groupe de commandes qui appartiennent à la fois (ajouter une colonne, supprimer une colonne, modifier la couleur de la ligne), puis placer ce groupe dans un sous-menu du menu contextuel de l’éditeur. L’extension repères de colonne ajoute également les commandes au menu **Edition** principal, mais les empêche de les masquer, comme le montre le modèle courant ci-dessous.

L’implémentation des commandes comporte trois parties : ColumnGuideCommandsPackage.cs, ColumnGuideCommandsPackage. vsct et ColumnGuideCommands.cs. Le code généré par les modèles met une commande dans le menu **Outils** qui affiche une boîte de dialogue en tant qu’implémentation. Vous pouvez voir comment cela est implémenté dans les fichiers. vsct et ColumnGuideCommands.cs, car il est assez simple. Vous allez remplacer le code dans les fichiers ci-dessous.

Le code du package est des déclarations réutilisables qui sont requises pour que Visual Studio découvre que l’extension offre des commandes et où placer les commandes. Lorsque le package est initialisé, il instancie la classe d’implémentation Commands. Pour plus d’informations sur les packages relatifs aux commandes, consultez le lien des commandes ci-dessus.

### <a name="a-common-commands-pattern"></a>Modèle de commandes courant
Les commandes de l’extension repères de colonne sont un exemple de modèle très courant dans Visual Studio. Vous placez les commandes associées dans un groupe et vous placez ce groupe dans un menu principal, souvent avec « `<CommandFlag>CommandWellOnly</CommandFlag>` » défini pour rendre la commande invisible. Le fait de placer des commandes dans les menus principaux (tels que **Edit**) de cette manière leur donne des noms intéressants (tels que **Edit. AddColumnGuide**) qui sont utiles pour rechercher des commandes lors de la réaffectation des combinaisons de touches dans les **Options des outils** et pour l’obtention de la saisie semi-automatique lors de l’appel de commandes à partir de la fenêtre de **commande**.

Vous ajoutez ensuite le groupe de commandes aux menus contextuels ou aux sous-menus où vous prévoyez que l’utilisateur utilise les commandes. Visual Studio traite `CommandWellOnly` comme un indicateur d’invisibilité pour les menus principaux uniquement. Lorsque vous placez le même groupe de commandes dans un menu contextuel ou sous-menu, les commandes sont visibles.

Dans le cadre du modèle commun, l’extension repères de colonne crée un deuxième groupe qui contient un seul sous-menu. Le sous-menu contient à son tour le premier groupe avec les quatre commandes du repère de colonne. Le deuxième groupe qui contient le sous-menu est la ressource réutilisable que vous placez dans différents menus contextuels, qui place un sous-menu sur ces menus contextuels.

### <a name="the-vsct-file"></a>Fichier. vsct
Le fichier. vsct déclare les commandes et leur emplacement, ainsi que les icônes, etc. Remplacez le contenu du fichier. vsct par le code suivant (indiqué ci-dessous) :

```xml
<?xml version="1.0" encoding="utf-8"?>
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">

  <!--  This is the file that defines the actual layout and type of the commands.
        It is divided in different sections (e.g. command definition, command
        placement, ...), with each defining a specific set of properties.
        See the comment before each section for more details about how to
        use it. -->

  <!--  The VSCT compiler (the tool that translates this file into the binary
        format that VisualStudio will consume) has the ability to run a preprocessor
        on the vsct file; this preprocessor is (usually) the C++ preprocessor, so
        it is possible to define includes and macros with the same syntax used
        in C++ files. Using this ability of the compiler here, we include some files
        defining some of the constants that we will use inside the file. -->

  <!--This is the file that defines the IDs for all the commands exposed by
      VisualStudio. -->
  <Extern href="stdidcmd.h"/>

  <!--This header contains the command ids for the menus provided by the shell. -->
  <Extern href="vsshlids.h"/>

  <!--The Commands section is where commands, menus, and menu groups are defined.
      This section uses a Guid to identify the package that provides the command
      defined inside it. -->
  <Commands package="guidColumnGuideCommandsPkg">
    <!-- Inside this section we have different sub-sections: one for the menus, another
    for the menu groups, one for the buttons (the actual commands), one for the combos
    and the last one for the bitmaps used. Each element is identified by a command id
    that is a unique pair of guid and numeric identifier; the guid part of the identifier
    is usually called "command set" and is used to group different command inside a
    logically related group; your package should define its own command set in order to
    avoid collisions with command ids defined by other packages. -->

    <!-- In this section you can define new menu groups. A menu group is a container for
         other menus or buttons (commands); from a visual point of view you can see the
         group as the part of a menu contained between two lines. The parent of a group
         must be a menu. -->
    <Groups>

      <!-- The main group is parented to the edit menu. All the buttons within the group
           have the "CommandWellOnly" flag, so they're actually invisible, but it means
           they get canonical names that begin with "Edit". Using placements, the group
           is also placed in the GuidesSubMenu group. -->
      <!-- The priority 0xB801 is chosen so it goes just after
           IDG_VS_EDIT_COMMANDWELL -->
      <Group guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
             priority="0xB801">
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_EDIT" />
      </Group>

      <!-- Group for holding the "Guidelines" sub-menu anchor (the item on the menu that
           drops the sub menu). The group is parented to
           the context menu for code windows. That takes care of most editors, but it's
           also placed in a couple of other windows using Placements -->
      <Group guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
             priority="0x0600">
        <Parent guid="guidSHLMainMenu" id="IDM_VS_CTXT_CODEWIN" />
      </Group>

    </Groups>

    <Menus>
      <Menu guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" priority="0x1000"
            type="Menu">
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup" />
        <Strings>
          <ButtonText>&Column Guides</ButtonText>
        </Strings>
      </Menu>
    </Menus>

    <!--Buttons section. -->
    <!--This section defines the elements the user can interact with, like a menu command or a button
        or combo box in a toolbar. -->
    <Buttons>
      <!--To define a menu group you have to specify its ID, the parent menu and its
          display priority.
          The command is visible and enabled by default. If you need to change the
          visibility, status, etc, you can use the CommandFlag node.
          You can add more than one CommandFlag node e.g.:
              <CommandFlag>DefaultInvisible</CommandFlag>
              <CommandFlag>DynamicVisibility</CommandFlag>
          If you do not want an image next to your command, remove the Icon node or
          set it to <Icon guid="guidOfficeIcon" id="msotcidNoIcon" /> -->

      <Button guid="guidColumnGuidesCommandSet" id="cmdidAddColumnGuide"
              priority="0x0100" type="Button">
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
        <Icon guid="guidImages" id="bmpPicAddGuide" />
        <CommandFlag>CommandWellOnly</CommandFlag>
        <CommandFlag>AllowParams</CommandFlag>
        <Strings>
          <ButtonText>&Add Column Guide</ButtonText>
        </Strings>
      </Button>

      <Button guid="guidColumnGuidesCommandSet" id="cmdidRemoveColumnGuide"
              priority="0x0101" type="Button">
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
        <Icon guid="guidImages" id="bmpPicRemoveGuide" />
        <CommandFlag>CommandWellOnly</CommandFlag>
        <CommandFlag>AllowParams</CommandFlag>
        <Strings>
          <ButtonText>&Remove Column Guide</ButtonText>
        </Strings>
      </Button>

      <Button guid="guidColumnGuidesCommandSet" id="cmdidChooseGuideColor"
              priority="0x0103" type="Button">
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
        <Icon guid="guidImages" id="bmpPicChooseColor" />
        <CommandFlag>CommandWellOnly</CommandFlag>
        <Strings>
          <ButtonText>Column Guide &Color...</ButtonText>
        </Strings>
      </Button>

      <Button guid="guidColumnGuidesCommandSet" id="cmdidRemoveAllColumnGuides"
              priority="0x0102" type="Button">
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
        <CommandFlag>CommandWellOnly</CommandFlag>
        <Strings>
          <ButtonText>Remove A&ll Columns</ButtonText>
        </Strings>
      </Button>
    </Buttons>

    <!--The bitmaps section is used to define the bitmaps that are used for the
        commands.-->
    <Bitmaps>
      <!--  The bitmap id is defined in a way that is a little bit different from the
            others:
            the declaration starts with a guid for the bitmap strip, then there is the
            resource id of the bitmap strip containing the bitmaps and then there are
            the numeric ids of the elements used inside a button definition. An important
            aspect of this declaration is that the element id
            must be the actual index (1-based) of the bitmap inside the bitmap strip. -->
      <Bitmap guid="guidImages" href="Resources\ColumnGuideCommands.png"
              usedList="bmpPicAddGuide, bmpPicRemoveGuide, bmpPicChooseColor" />
    </Bitmaps>

  </Commands>

  <CommandPlacements>

    <!-- Define secondary placements for our groups -->

    <!-- Place the group containing the three commands in the sub-menu -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
                      priority="0x0100">
      <Parent guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" />
    </CommandPlacement>

    <!-- The HTML editor context menu, for some reason, redefines its own groups
         so we need to place a copy of our context menu there too. -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
                      priority="0x1001">
      <Parent guid="CMDSETID_HtmEdGrp" id="IDMX_HTM_SOURCE_HTML" />
    </CommandPlacement>

    <!-- The HTML context menu in Dev12 changed. -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
                      priority="0x1001">
      <Parent guid="CMDSETID_HtmEdGrp_Dev12" id="IDMX_HTM_SOURCE_HTML_Dev12" />
    </CommandPlacement>

    <!-- Similarly for Script -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
                      priority="0x1001">
      <Parent guid="CMDSETID_HtmEdGrp" id="IDMX_HTM_SOURCE_SCRIPT" />
    </CommandPlacement>

    <!-- Similarly for ASPX  -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
                      priority="0x1001">
      <Parent guid="CMDSETID_HtmEdGrp" id="IDMX_HTM_SOURCE_ASPX" />
    </CommandPlacement>

    <!-- Similarly for the XAML editor context menu -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
                      priority="0x0600">
      <Parent guid="guidXamlUiCmds" id="IDM_XAML_EDITOR" />
    </CommandPlacement>

  </CommandPlacements>

  <!-- This defines the identifiers and their values used above to index resources
       and specify commands. -->
  <Symbols>
    <!-- This is the package guid. -->
    <GuidSymbol name="guidColumnGuideCommandsPkg"
                value="{e914e5de-0851-4904-b361-1a3a9d449704}" />

    <!-- This is the guid used to group the menu commands together -->
    <GuidSymbol name="guidColumnGuidesCommandSet"
                value="{c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e}">
      <IDSymbol name="GuidesContextMenuGroup" value="0x1020" />
      <IDSymbol name="GuidesMenuItemsGroup" value="0x1021" />
      <IDSymbol name="GuidesSubMenu" value="0x1022" />
      <IDSymbol name="cmdidAddColumnGuide" value="0x0100" />
      <IDSymbol name="cmdidRemoveColumnGuide" value="0x0101" />
      <IDSymbol name="cmdidChooseGuideColor" value="0x0102" />
      <IDSymbol name="cmdidRemoveAllColumnGuides" value="0x0103" />
    </GuidSymbol>

    <GuidSymbol name="guidImages" value="{2C99F852-587C-43AF-AA2D-F605DE2E46EF}">
      <IDSymbol name="bmpPicAddGuide" value="1" />
      <IDSymbol name="bmpPicRemoveGuide" value="2" />
      <IDSymbol name="bmpPicChooseColor" value="3" />
    </GuidSymbol>

    <GuidSymbol name="CMDSETID_HtmEdGrp_Dev12"
                value="{78F03954-2FB8-4087-8CE7-59D71710B3BB}">
      <IDSymbol name="IDMX_HTM_SOURCE_HTML_Dev12" value="0x1" />
    </GuidSymbol>

    <GuidSymbol name="CMDSETID_HtmEdGrp" value="{d7e8c5e1-bdb8-11d0-9c88-0000f8040a53}">
      <IDSymbol name="IDMX_HTM_SOURCE_HTML" value="0x33" />
      <IDSymbol name="IDMX_HTM_SOURCE_SCRIPT" value="0x34" />
      <IDSymbol name="IDMX_HTM_SOURCE_ASPX" value="0x35" />
    </GuidSymbol>

    <GuidSymbol name="guidXamlUiCmds" value="{4c87b692-1202-46aa-b64c-ef01faec53da}">
      <IDSymbol name="IDM_XAML_EDITOR" value="0x103" />
    </GuidSymbol>
  </Symbols>

</CommandTable>

```

**GUID**. Pour permettre à Visual Studio de rechercher vos gestionnaires de commandes et de les appeler, vous devez vous assurer que le GUID du package déclaré dans le fichier ColumnGuideCommandsPackage.cs (généré à partir du modèle d’élément de projet) correspond au GUID du package déclaré dans le fichier. vsct (copié à partir de la version ci-dessus). Si vous réutilisez cet exemple de code, vous devez vous assurer que vous disposez d’un GUID différent afin de ne pas entrer en conflit avec les autres personnes qui ont peut-être copié ce code.

Recherchez cette ligne dans ColumnGuideCommandsPackage.cs et copiez le GUID entre les guillemets :

```csharp
public const string PackageGuidString = "ef726849-5447-4f73-8de5-01b9e930f7cd";
```

Collez ensuite le GUID dans le fichier. vsct afin d’obtenir la ligne suivante dans vos `Symbols` déclarations :

```xml
<GuidSymbol name="guidColumnGuideCommandsPkg" 
            value="{ef726849-5447-4f73-8de5-01b9e930f7cd}" />
```

Les GUID pour le jeu de commandes et le fichier image bitmap doivent également être uniques pour vos extensions :

```xml
<GuidSymbol name="guidColumnGuidesCommandSet"
            value="{c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e}">
<GuidSymbol name="guidImages" value="{2C99F852-587C-43AF-AA2D-F605DE2E46EF}">
```

Toutefois, vous n’avez pas besoin de modifier le jeu de commandes et les GUID d’image bitmap dans cette procédure pas à pas pour que le code fonctionne. Le GUID du jeu de commandes doit correspondre à la déclaration dans le fichier ColumnGuideCommands.cs, mais vous allez également remplacer le contenu de ce fichier. par conséquent, les GUID correspondent.

D’autres GUID dans le fichier. vsct identifient les menus préexistants auxquels les commandes de guide de colonne sont ajoutées, afin qu’elles ne changent jamais.

**Sections de fichier**. Le. vsct comporte trois sections externes : commandes, placements et symboles. La section commandes définit des groupes de commandes, des menus, des boutons ou des éléments de menu et des bitmaps pour les icônes. La section positionnements déclare où les groupes se trouvent dans des menus ou des emplacements supplémentaires sur des menus préexistants. La section Symbols déclare les identificateurs utilisés ailleurs dans le fichier. vsct, ce qui rend le code. vsct plus lisible que les GUID et les nombres hexadécimaux partout.

**Section commandes, définitions de groupes**. La section Commands définit tout d’abord les groupes de commandes. Les groupes de commandes sont des commandes qui s’affichent dans les menus avec de légers traits gris séparés par des groupes. Un groupe peut également remplir un sous-menu entier, comme dans cet exemple, et vous ne voyez pas les lignes de séparation grises dans ce cas. Les fichiers. vsct déclarent deux groupes, le `GuidesMenuItemsGroup` qui est apparenté au `IDM_VS_MENU_EDIT` (menu **édition** principal) et le `GuidesContextMenuGroup` qui est apparenté au `IDM_VS_CTXT_CODEWIN` (menu contextuel de l’éditeur de code).

La deuxième déclaration de groupe a une `0x0600` priorité :

```xml
<Group guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
             priority="0x0600">
```

L’idée est de placer le sous-menu repères de colonne à la fin de n’importe quel menu contextuel auquel nous ajoutons le groupe de sous-menu. Toutefois, vous ne devez pas supposer que vous connaissez le mieux et forcer le sous-menu à toujours être le dernier en utilisant une priorité de `0xFFFF` . Vous devez lire ce nombre pour voir où votre sous-menu se trouve dans les menus contextuels où vous le placez. Dans ce cas `0x0600` , est suffisamment élevé pour le placer à la fin des menus comme nous pouvons le voir, mais elle laisse de l’espace pour qu’une autre personne puisse concevoir son extension pour qu’elle soit inférieure à l’extension repères de colonne si cela est souhaitable.

**Section commandes, définition de menu**. La section commande définit ensuite le sous-menu `GuidesSubMenu` , apparenté à `GuidesContextMenuGroup` . `GuidesContextMenuGroup`Est le groupe que nous ajoutons à tous les menus contextuels pertinents. Dans la section positionnements, le code place le groupe avec les quatre commandes du repère de colonne dans ce sous-menu.

**Section commandes, définitions de boutons**. La section commandes définit ensuite les éléments de menu ou les boutons qui sont les quatre commandes de repères de colonne. `CommandWellOnly`, comme indiqué ci-dessus, signifie que les commandes sont invisibles lorsqu’elles sont placées dans un menu principal. Deux des déclarations de bouton d’élément de menu (ajouter un guide et supprimer le guide) ont également un `AllowParams` indicateur :

```xml
<CommandFlag>AllowParams</CommandFlag>
```

Cet indicateur active, ainsi que les emplacements de menu principal, la commande pour recevoir des arguments quand Visual Studio appelle le gestionnaire de commandes. Si l’utilisateur appelle la commande à partir de la fenêtre commande, l’argument est passé au gestionnaire de commandes dans les arguments de l’événement.

**Sections de commande, définitions bitmaps**. Enfin, la section Commands déclare les bitmaps ou les icônes utilisées pour les commandes. Il s’agit d’une déclaration simple qui identifie la ressource de projet et répertorie les index de base 1 des icônes utilisées. La section Symbols du fichier. vsct déclare les valeurs des identificateurs utilisés comme index. Cette procédure pas à pas utilise la bande bitmap fournie avec le modèle d’élément de commande personnalisé ajouté au projet.

**Section placements**. Une fois que la section Commands est la section emplacements. La première est celle où le code ajoute le premier groupe abordé ci-dessus, qui contient les quatre commandes de guide de colonne au sous-menu où les commandes apparaissent :

```xml
<CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
                  priority="0x0100">
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" />
</CommandPlacement>
```

Tous les autres emplacements ajoutent le `GuidesContextMenuGroup` (qui contient le `GuidesSubMenu` ) à d’autres menus contextuels de l’éditeur. Lorsque le code a déclaré le `GuidesContextMenuGroup` , il a été apparenté au menu contextuel de l’éditeur de code. C’est pourquoi vous ne voyez pas d’emplacement pour le menu contextuel de l’éditeur de code.

**Section de symboles**. Comme indiqué ci-dessus, la section Symbols déclare des identificateurs utilisés ailleurs dans le fichier. vsct, ce qui rend le code. vsct plus lisible que les GUID et les nombres hexadécimaux partout. Les points importants de cette section sont que le GUID du package doit être conforme à la déclaration dans la classe de package et que le GUID du jeu de commandes doit accepter la déclaration dans la classe d’implémentation de la commande.

## <a name="implementing-the-commands"></a>Implémentation des commandes
Le fichier ColumnGuideCommands.cs implémente les commandes et raccorde les gestionnaires. Lorsque Visual Studio charge le package et l’initialise, le package appelle à son tour la `Initialize` classe d’implémentation des commandes. L’initialisation des commandes instancie simplement la classe et le constructeur raccorde tous les gestionnaires de commandes.

Remplacez le contenu du fichier ColumnGuideCommands.cs par le code suivant (indiqué ci-dessous) :

```csharp
using System;
using System.ComponentModel.Design;
using System.Globalization;
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.Shell.Interop;
using Microsoft.VisualStudio.TextManager.Interop;
using Microsoft.VisualStudio.Text.Editor;
using Microsoft.VisualStudio;

namespace ColumnGuides
{
    /// <summary>
    /// Command handler
    /// </summary>
    internal sealed class ColumnGuideCommands
    {

        const int cmdidAddColumnGuide = 0x0100;
        const int cmdidRemoveColumnGuide = 0x0101;
        const int cmdidChooseGuideColor = 0x0102;
        const int cmdidRemoveAllColumnGuides = 0x0103;

        /// <summary>
        /// Command menu group (command set GUID).
        /// </summary>
        static readonly Guid CommandSet =
            new Guid("c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e");

        /// <summary>
        /// VS Package that provides this command, not null.
        /// </summary>
        private readonly Package package;

        OleMenuCommand _addGuidelineCommand;
        OleMenuCommand _removeGuidelineCommand;

        /// <summary>
        /// Initializes the singleton instance of the command.
        /// </summary>
        /// <param name="package">Owner package, not null.</param>
        public static void Initialize(Package package)
        {
            Instance = new ColumnGuideCommands(package);
        }

        /// <summary>
        /// Gets the instance of the command.
        /// </summary>
        public static ColumnGuideCommands Instance
        {
            get;
            private set;
        }

        /// <summary>
        /// Initializes a new instance of the <see cref="ColumnGuideCommands"/> class.
        /// Adds our command handlers for menu (commands must exist in the command
        /// table file)
        /// </summary>
        /// <param name="package">Owner package, not null.</param>
        private ColumnGuideCommands(Package package)
        {
            if (package == null)
            {
                throw new ArgumentNullException("package");
            }

            this.package = package;

            // Add our command handlers for menu (commands must exist in the .vsct file)

            OleMenuCommandService commandService =
                this.ServiceProvider.GetService(typeof(IMenuCommandService))
                    as OleMenuCommandService;
            if (commandService != null)
            {
                // Add guide
                _addGuidelineCommand =
                    new OleMenuCommand(AddColumnGuideExecuted, null,
                                       AddColumnGuideBeforeQueryStatus,
                                       new CommandID(ColumnGuideCommands.CommandSet,
                                                     cmdidAddColumnGuide));
                _addGuidelineCommand.ParametersDescription = "<column>";
                commandService.AddCommand(_addGuidelineCommand);
                // Remove guide
                _removeGuidelineCommand =
                    new OleMenuCommand(RemoveColumnGuideExecuted, null,
                                       RemoveColumnGuideBeforeQueryStatus,
                                       new CommandID(ColumnGuideCommands.CommandSet,
                                                     cmdidRemoveColumnGuide));
                _removeGuidelineCommand.ParametersDescription = "<column>";
                commandService.AddCommand(_removeGuidelineCommand);
                // Choose color
                commandService.AddCommand(
                    new MenuCommand(ChooseGuideColorExecuted,
                                    new CommandID(ColumnGuideCommands.CommandSet,
                                                  cmdidChooseGuideColor)));
                // Remove all
                commandService.AddCommand(
                    new MenuCommand(RemoveAllGuidelinesExecuted,
                                    new CommandID(ColumnGuideCommands.CommandSet,
                                                  cmdidRemoveAllColumnGuides)));
            }
        }

        /// <summary>
        /// Gets the service provider from the owner package.
        /// </summary>
        private IServiceProvider ServiceProvider
        {
            get
            {
                return this.package;
            }
        }

        private void AddColumnGuideBeforeQueryStatus(object sender, EventArgs e)
        {
            int currentColumn = GetCurrentEditorColumn();
            _addGuidelineCommand.Enabled =
                GuidesSettingsManager.CanAddGuideline(currentColumn);
        }

        private void RemoveColumnGuideBeforeQueryStatus(object sender, EventArgs e)
        {
            int currentColumn = GetCurrentEditorColumn();
            _removeGuidelineCommand.Enabled =
                GuidesSettingsManager.CanRemoveGuideline(currentColumn);
        }

        private int GetCurrentEditorColumn()
        {
            IVsTextView view = GetActiveTextView();
            if (view == null)
            {
                return -1;
            }

            try
            {
                IWpfTextView textView = GetTextViewFromVsTextView(view);
                int column = GetCaretColumn(textView);

                // Note: GetCaretColumn returns 0-based positions. Guidelines are 1-based
                // positions.
                // However, do not subtract one here since the caret is positioned to the
                // left of
                // the given column and the guidelines are positioned to the right. We
                // want the
                // guideline to line up with the current caret position. e.g. When the
                // caret is
                // at position 1 (zero-based), the status bar says column 2. We want to
                // add a
                // guideline for column 1 since that will place the guideline where the
                // caret is.
                return column;
            }
            catch (InvalidOperationException)
            {
                return -1;
            }
        }

        /// <summary>
        /// Find the active text view (if any) in the active document.
        /// </summary>
        /// <returns>The IVsTextView of the active view, or null if there is no active
        /// document or the
        /// active view in the active document is not a text view.</returns>
        private IVsTextView GetActiveTextView()
        {
            IVsMonitorSelection selection =
                this.ServiceProvider.GetService(typeof(IVsMonitorSelection))
                                                    as IVsMonitorSelection;
            object frameObj = null;
            ErrorHandler.ThrowOnFailure(
                selection.GetCurrentElementValue(
                    (uint)VSConstants.VSSELELEMID.SEID_DocumentFrame, out frameObj));

            IVsWindowFrame frame = frameObj as IVsWindowFrame;
            if (frame == null)
            {
                return null;
            }

            return GetActiveView(frame);
        }

        private static IVsTextView GetActiveView(IVsWindowFrame windowFrame)
        {
            if (windowFrame == null)
            {
                throw new ArgumentException("windowFrame");
            }

            object pvar;
            ErrorHandler.ThrowOnFailure(
                windowFrame.GetProperty((int)__VSFPROPID.VSFPROPID_DocView, out pvar));

            IVsTextView textView = pvar as IVsTextView;
            if (textView == null)
            {
                IVsCodeWindow codeWin = pvar as IVsCodeWindow;
                if (codeWin != null)
                {
                    ErrorHandler.ThrowOnFailure(codeWin.GetLastActiveView(out textView));
                }
            }
            return textView;
        }

        private static IWpfTextView GetTextViewFromVsTextView(IVsTextView view)
        {

            if (view == null)
            {
                throw new ArgumentNullException("view");
            }

            IVsUserData userData = view as IVsUserData;
            if (userData == null)
            {
                throw new InvalidOperationException();
            }

            object objTextViewHost;
            if (VSConstants.S_OK
                   != userData.GetData(Microsoft.VisualStudio
                                                .Editor
                                                .DefGuidList.guidIWpfTextViewHost,
                                       out objTextViewHost))
            {
                throw new InvalidOperationException();
            }

            IWpfTextViewHost textViewHost = objTextViewHost as IWpfTextViewHost;
            if (textViewHost == null)
            {
                throw new InvalidOperationException();
            }

            return textViewHost.TextView;
        }

        /// <summary>
        /// Given an IWpfTextView, find the position of the caret and report its column
        /// number. The column number is 0-based
        /// </summary>
        /// <param name="textView">The text view containing the caret</param>
        /// <returns>The column number of the caret's position. When the caret is at the
        /// leftmost column, the return value is zero.</returns>
        private static int GetCaretColumn(IWpfTextView textView)
        {
            // This is the code the editor uses to populate the status bar.
            Microsoft.VisualStudio.Text.Formatting.ITextViewLine caretViewLine =
                textView.Caret.ContainingTextViewLine;
            double columnWidth = textView.FormattedLineSource.ColumnWidth;
            return (int)(Math.Round((textView.Caret.Left - caretViewLine.Left)
                                       / columnWidth));
        }

        /// <summary>
        /// Determine the applicable column number for an add or remove command.
        /// The column is parsed from command arguments, if present. Otherwise
        /// the current position of the caret is used to determine the column.
        /// </summary>
        /// <param name="e">Event args passed to the command handler.</param>
        /// <returns>The column number. May be negative to indicate the column number is
        /// unavailable.</returns>
        /// <exception cref="ArgumentException">The column number parsed from event args
        /// was not a valid integer.</exception>
        private int GetApplicableColumn(EventArgs e)
        {
            var inValue = ((OleMenuCmdEventArgs)e).InValue as string;
            if (!string.IsNullOrEmpty(inValue))
            {
                int column;
                if (!int.TryParse(inValue, out column) || column < 0)
                    throw new ArgumentException("Invalid column");
                return column;
            }

            return GetCurrentEditorColumn();
        }

        /// <summary>
        /// This function is the callback used to execute a command when the a menu item
        /// is clicked. See the Initialize method to see how the menu item is associated
        /// to this function using the OleMenuCommandService service and the MenuCommand
        /// class.
        /// </summary>
        private void AddColumnGuideExecuted(object sender, EventArgs e)
        {
            int column = GetApplicableColumn(e);
            if (column >= 0)
            {
                GuidesSettingsManager.AddGuideline(column);
            }
        }

        private void RemoveColumnGuideExecuted(object sender, EventArgs e)
        {
            int column = GetApplicableColumn(e);
            if (column >= 0)
            {
                GuidesSettingsManager.RemoveGuideline(column);
            }
        }

        private void RemoveAllGuidelinesExecuted(object sender, EventArgs e)
        {
            GuidesSettingsManager.RemoveAllGuidelines();
        }

        private void ChooseGuideColorExecuted(object sender, EventArgs e)
        {
            System.Windows.Media.Color color = GuidesSettingsManager.GuidelinesColor;

            using (System.Windows.Forms.ColorDialog picker =
                new System.Windows.Forms.ColorDialog())
            {
                picker.Color = System.Drawing.Color.FromArgb(255, color.R, color.G,
                                                             color.B);
                if (picker.ShowDialog() == System.Windows.Forms.DialogResult.OK)
                {
                    GuidesSettingsManager.GuidelinesColor =
                        System.Windows.Media.Color.FromRgb(picker.Color.R,
                                                           picker.Color.G,
                                                           picker.Color.B);
                }
            }
        }

    }
}

```

**Corriger les références**. Il manque une référence à ce stade. Appuyez sur le bouton de pointeur droit sur le nœud références dans le Explorateur de solutions. Choisissez l' **Ajout...** . La boîte de dialogue **Ajouter une référence** comporte une zone de recherche dans le coin supérieur droit. Entrez « éditeur » (sans les guillemets doubles). Choisissez l’élément **Microsoft. VisualStudio. Editor** (vous devez activer la case à cocher à gauche de l’élément, et non simplement l’élément), puis choisissez **OK** pour ajouter la référence.

**Initialisation**. Quand la classe de package est initialisée, elle appelle `Initialize` la classe d’implémentation Commands. L' `ColumnGuideCommands` initialisation instancie la classe et enregistre l’instance de classe et la référence de package dans les membres de la classe.

Examinons l’un des raccordements du gestionnaire de commandes à partir du constructeur de classe :

```csharp
_addGuidelineCommand =
    new OleMenuCommand(AddColumnGuideExecuted, null,
                       AddColumnGuideBeforeQueryStatus,
                       new CommandID(ColumnGuideCommands.CommandSet,
                                     cmdidAddColumnGuide));

```

Vous créez un `OleMenuCommand` . Visual Studio utilise le système de commande Microsoft Office. Les arguments clés lors de l’instanciation d’un OleMenuCommand sont la fonction qui implémente la commande ( `AddColumnGuideExecuted` ), la fonction à appeler quand Visual Studio affiche un menu avec la commande ( `AddColumnGuideBeforeQueryStatus` ) et l’ID de commande. Visual Studio appelle la fonction d’état de la requête avant d’afficher une commande dans un menu afin que la commande puisse se rendre invisible ou grisée pour un affichage particulier du menu (par exemple, en désactivant la **copie** s’il n’y a aucune sélection), changer son icône ou même changer son nom (par exemple, ajouter un élément à supprimer un élément), et ainsi de suite. L’ID de commande doit correspondre à un ID de commande déclaré dans le fichier. vsct. Les chaînes pour le jeu de commandes et la commande Ajouter des repères de colonne doivent correspondre entre le fichier. vsct et le ColumnGuideCommands.cs.

La ligne suivante fournit une assistance pour les cas où les utilisateurs appellent la commande par le biais de la fenêtre commande (comme indiqué ci-dessous) :

```csharp
_addGuidelineCommand.ParametersDescription = "<column>";
```

**État**de la requête. Les fonctions d’état `AddColumnGuideBeforeQueryStatus` de la requête et `RemoveColumnGuideBeforeQueryStatus` vérifient certains paramètres (par exemple, le nombre maximal de guides ou la colonne max) ou s’il existe un repère de colonne à supprimer. Ils activent les commandes si les conditions sont correctes. Les fonctions d’état de la requête doivent être très efficaces, car elles s’exécutent chaque fois que Visual Studio affiche un menu, pour chaque commande du menu.

**Fonction AddColumnGuideExecuted**. La partie intéressante de l’ajout d’un guide consiste à déterminer la vue actuelle de l’éditeur et l’emplacement du signe insertion. Tout d’abord, cette fonction appelle `GetApplicableColumn` qui vérifie s’il existe un argument fourni par l’utilisateur dans les arguments d’événement du gestionnaire de commandes et, s’il n’en existe aucun, la fonction vérifie la vue de l’éditeur :

```csharp
private int GetApplicableColumn(EventArgs e)
{
    var inValue = ((OleMenuCmdEventArgs)e).InValue as string;
    if (!string.IsNullOrEmpty(inValue))
    {
        int column;
        if (!int.TryParse(inValue, out column) || column < 0)
            throw new ArgumentException("Invalid column");
        return column;
    }

    return GetCurrentEditorColumn();
}

```

`GetCurrentEditorColumn` doit approfondir un peu pour obtenir une <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> vue du code. Si vous `GetActiveTextView` `GetActiveView` effectuez le suivi, et `GetTextViewFromVsTextView` , vous pouvez voir comment procéder. Voici le code abstrait, en commençant par la sélection actuelle, puis en obtenant le frame de la sélection, puis en obtenant le DocView du frame en tant que <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> , en obtenant un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> à partir du IVsTextView, en obtenant un hôte de vue et enfin le IWpfTextView :

```csharp
   IVsMonitorSelection selection =
       this.ServiceProvider.GetService(typeof(IVsMonitorSelection))
           as IVsMonitorSelection;
   object frameObj = null;

ErrorHandler.ThrowOnFailure(selection.GetCurrentElementValue(
                                (uint)VSConstants.VSSELELEMID.SEID_DocumentFrame,
                                out frameObj));

   IVsWindowFrame frame = frameObj as IVsWindowFrame;
   if (frame == null)
       <<do nothing>>;

...
   object pvar;
   ErrorHandler.ThrowOnFailure(frame.GetProperty((int)__VSFPROPID.VSFPROPID_DocView,
                                                  out pvar));

   IVsTextView textView = pvar as IVsTextView;
   if (textView == null)
   {
       IVsCodeWindow codeWin = pvar as IVsCodeWindow;
       if (codeWin != null)
       {
           ErrorHandler.ThrowOnFailure(codeWin.GetLastActiveView(out textView));
       }
   }

...
   if (textView == null)
       <<do nothing>>

   IVsUserData userData = textView as IVsUserData;
   if (userData == null)
       <<do nothing>>

   object objTextViewHost;
   if (VSConstants.S_OK
           != userData.GetData(Microsoft.VisualStudio.Editor.DefGuidList
                                                            .guidIWpfTextViewHost,
                                out objTextViewHost))
   {
       <<do nothing>>
   }

   IWpfTextViewHost textViewHost = objTextViewHost as IWpfTextViewHost;
   if (textViewHost == null)
       <<do nothing>>

   IWpfTextView textView = textViewHost.TextView;

```

Une fois que vous disposez d’un IWpfTextView, vous pouvez obtenir la colonne dans laquelle se trouve le signe insertion :

```csharp
private static int GetCaretColumn(IWpfTextView textView)
{
    // This is the code the editor uses to populate the status bar.
    Microsoft.VisualStudio.Text.Formatting.ITextViewLine caretViewLine =
        textView.Caret.ContainingTextViewLine;
    double columnWidth = textView.FormattedLineSource.ColumnWidth;
    return (int)(Math.Round((textView.Caret.Left - caretViewLine.Left)
                                / columnWidth));
}

```

Une fois que l’utilisateur a cliqué sur la colonne actuelle, le code appelle simplement le gestionnaire de paramètres pour ajouter ou supprimer la colonne. Le gestionnaire de paramètres déclenche l’événement dans lequel tous les `ColumnGuideAdornment` objets écoutent. Lorsque l’événement se déclenche, ces objets mettent à jour leurs affichages de texte associés avec les nouveaux paramètres du repère de colonne.

## <a name="invoking-command-from-the-command-window"></a>Appel de commande à partir de la fenêtre commande
L’exemple repères de colonne permet aux utilisateurs d’appeler deux commandes à partir de la fenêtre de commande sous forme d’extensibilité. Si vous utilisez la commande **afficher &#124; autres fenêtres commande Windows &#124;** , vous pouvez voir la fenêtre de commande. Vous pouvez interagir avec la fenêtre de commande en entrant « Edit », et avec la saisie semi-automatique du nom de la commande et en fournissant l’argument 120, vous disposez des éléments suivants :

```
> Edit.AddColumnGuide 120
>
```

Les parties de l’exemple qui permettent cela se trouvent dans les déclarations de fichier. vsct, le `ColumnGuideCommands` constructeur de classe lorsqu’il raccorde des gestionnaires de commandes et les implémentations du gestionnaire de commandes qui vérifient les arguments d’événement.

Vous avez vu « `<CommandFlag>CommandWellOnly</CommandFlag>` » dans le fichier. vsct, ainsi que les emplacements dans le menu Edition principal, même si nous n’affichons pas les commandes dans l’interface utilisateur du menu **Edition** . Leur présence dans le menu Edition principal leur donne des noms tels que **Edit. AddColumnGuide**. La déclaration de groupe commandes qui contient les quatre commandes ont placé le groupe dans le menu Edition directement :

```xml
<Group guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
             priority="0xB801">
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_EDIT" />
      </Group>

```

La section Buttons a ensuite déclaré les commandes `CommandWellOnly` pour les masquer dans le menu principal et les avoir déclarées avec `AllowParams` :

```xml
<Button guid="guidColumnGuidesCommandSet" id="cmdidAddColumnGuide" 
        priority="0x0100" type="Button">
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
  <Icon guid="guidImages" id="bmpPicAddGuide" />
  <CommandFlag>CommandWellOnly</CommandFlag>
  <CommandFlag>AllowParams</CommandFlag>

```

Vous avez vu le code de raccordement du gestionnaire de commandes dans le `ColumnGuideCommands` constructeur de classe fourni une description du paramètre autorisé :

```csharp
_addGuidelineCommand.ParametersDescription = "<column>";

```

Vous avez vu que la `GetApplicableColumn` fonction recherche `OleMenuCmdEventArgs` une valeur avant de vérifier la vue de l’éditeur pour une colonne actuelle :

```csharp
private int GetApplicableColumn(EventArgs e)
{
    var inValue = ((OleMenuCmdEventArgs)e).InValue as string;
    if (!string.IsNullOrEmpty(inValue))
    {
        int column;
        if (!int.TryParse(inValue, out column) || column < 0)
            throw new ArgumentException("Invalid column");
        return column;
    }

```

## <a name="trying-your-extension"></a>Essai de votre extension
Vous pouvez maintenant appuyer sur **F5** pour exécuter votre extension repères de colonnes. Ouvrez un fichier texte et utilisez le menu contextuel de l’éditeur pour ajouter des lignes de repère, les supprimer et modifier leur couleur. Vous devez cliquer dans le texte (et non pas sur l’espace blanc à la fin de la ligne) pour ajouter un repère de colonne, ou l’éditeur l’ajoute à la dernière colonne de la ligne. Si vous utilisez la fenêtre de commande et appelez les commandes avec un argument, vous pouvez ajouter des repères de colonne n’importe où.

Si vous souhaitez essayer différents placements de commandes, modifier des noms, changer d’icône, etc. et que vous avez des problèmes avec Visual Studio qui vous montrent le code le plus récent dans les menus, vous pouvez réinitialiser la ruche expérimentale dans laquelle vous effectuez le débogage. Ouvrez le **menu Démarrer de Windows** et tapez « réinitialiser ». Recherchez et appelez la commande **Réinitialiser la prochaine instance expérimentale de Visual Studio**. Cela nettoie la ruche de Registre expérimentale de tous les composants d’extension. Il n’efface pas les paramètres des composants. par conséquent, tous les guides dont vous disposiez lors de l’arrêt de la ruche expérimentale de Visual Studio sont toujours là quand votre code lit le magasin de paramètres au prochain lancement.

## <a name="finished-code-project"></a>Projet de code terminé
Il y aura bientôt un projet GitHub d’exemples d’extensibilité Visual Studio et le projet terminé sera présent. Nous mettrons à jour cette rubrique pour la faire pointer lorsque cela se produit. L’exemple de projet terminé peut avoir des GUID différents et disposer d’une bande bitmaps différente pour les icônes de commande.

Vous pouvez essayer une version de la fonctionnalité repères de colonne avec cette[extension](https://visualstudiogallery.msdn.microsoft.com/da227a0b-0e31-4a11-8f6b-3a149cf2e459?SRC=Home)de la Galerie Visual Studio.

## <a name="see-also"></a>Voir aussi
[Dans l’éditeur](../extensibility/inside-the-editor.md) 
 [Extension de l’éditeur et des services](../extensibility/extending-the-editor-and-language-services.md) 
 de langage Points d’extension du [service de langage et de l’éditeur](../extensibility/language-service-and-editor-extension-points.md) 
 [Extension des menus et des commandes](../extensibility/extending-menus-and-commands.md) 
 [Ajout d’un sous-menu à un menu](../extensibility/adding-a-submenu-to-a-menu.md) 
 [Création d’une extension avec un modèle d’élément d’éditeur](../extensibility/creating-an-extension-with-an-editor-item-template.md)
