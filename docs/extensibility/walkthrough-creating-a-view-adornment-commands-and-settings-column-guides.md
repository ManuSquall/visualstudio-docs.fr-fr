---
title: Création d’une ornement de vue, de commandes et de paramètres . Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4a2df0a3-42da-4f7b-996f-ee16a35ac922
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4aab9e0ede95eebe6f8f54cc3f01e7e7d5f98d1c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697645"
---
# <a name="walkthrough-create-a-view-adornment-commands-and-settings-column-guides"></a>Procédure pas à pas : Créez une parure de vue, des commandes et des paramètres (guides de colonne)
Vous pouvez étendre l’éditeur de texte/code Visual Studio avec commandes et effets de vue. Cet article vous montre comment commencer avec une fonction d’extension populaire, guides de colonnes. Les guides de colonne sont des lignes visuellement légères dessinées sur la vue de l’éditeur de texte pour vous aider à gérer votre code à des largeurs de colonne spécifiques. Plus précisément, le code formaté peut être important pour les échantillons que vous incluez dans les documents, les billets de blog ou les rapports de bogues.

Lors de cette procédure pas à pas, vous allez effectuer les opérations suivantes :
- Créer un projet VSIX
- Ajouter une parure de vue d’éditeur
- Ajoutez un support pour enregistrer et obtenir des paramètres (où dessiner des guides de colonne et leur couleur)
- Ajouter des commandes (ajouter/supprimer les guides de colonne, changer de couleur)
- Placez les commandes sur le menu Edit et les menus contextuels de documents texte
- Ajoutez un support pour invoquer les commandes de la fenêtre de commande de studio visuel

  Vous pouvez essayer une version de la fonction guides de colonne avec cette[extension](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.EditorGuidelines)Visual Studio Gallery .

  > [!NOTE]
  > Dans cette procédure pas à pas, vous collez une grande quantité de code dans quelques fichiers générés par les modèles d’extension Visual Studio. Mais, bientôt cette procédure pas à pas se référera à une solution complète sur GitHub avec d’autres exemples d’extension. Le code terminé est légèrement différent en ce qu’il a de véritables icônes de commande au lieu d’utiliser des icônes génériques.

## <a name="get-started"></a>Bien démarrer
A partir de Visual Studio 2015, vous n’installez pas le Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme une fonctionnalité facultative dans la configuration Visual Studio. Vous pouvez également installer le VS SDK plus tard. Pour plus d’informations, voir [Installer le Studio Visuel SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="set-up-the-solution"></a>Configurer la solution
Tout d’abord, vous créez un projet VSIX, ajoutez une parure de vue d’éditeur, puis ajoutez une commande (qui ajoute un VSPackage pour posséder la commande). L’architecture de base est la suivante:
- Vous avez un auditeur de création `ColumnGuideAdornment` de vue de texte qui crée un objet par vue. Cet objet est à l’écoute des événements concernant le changement de vue ou les paramètres changeant, mettant à jour ou redessinant les guides de colonne au besoin.
- Il ya `GuidesSettingsManager` un qui gère la lecture et l’écriture à partir du stockage des paramètres Visual Studio. Le gestionnaire des paramètres dispose également d’opérations de mise à jour des paramètres qui prennent en charge les commandes de l’utilisateur (ajouter la colonne, supprimer la colonne, changer de couleur).
- Il ya un paquet VSIP qui est nécessaire si vous avez des commandes utilisateur, mais c’est juste le code de la plaque chauffante qui initialise l’objet de mise en œuvre des commandes.
- Il y `ColumnGuideCommands` a un objet qui exécute les commandes de l’utilisateur et accroche les gestionnaires de commande pour les commandes déclarées dans le fichier *.vsct.*

  **VSIX**. Utilisez **File &#124; Nouvelle commande ...** pour créer un projet. Choisissez le nœud **Extensibility** sous **le** volet de navigation gauche et choisissez **le projet VSIX** dans le volet droit. Entrez le nom **ColumnGuides** et choisissez **OK** pour créer le projet.

  **Voir l’ornement .** Appuyez sur le bouton pointeur droit sur le nœud de projet dans l’explorer de solution. Choisissez **l’ajouter &#124; nouvel article ...** commande pour ajouter un nouvel élément d’ornement de vue. Choisissez **Extensibility &#124; Editor** dans le volet de navigation gauche et choisissez **l’éditeur Viewport Adornment** dans le volet droit. Entrez le nom **ColumnGuideAdornment** comme nom de l’élément et choisissez **Ajouter** pour l’ajouter.

  Vous pouvez voir ce modèle d’élément ajouté deux fichiers au projet (ainsi que des références, et ainsi de suite): **ColumnGuideAdornment.cs** et **ColumnGuideAdornmentTextViewCreationListener.cs**. Les modèles dessinent un rectangle violet sur la vue. Dans la section suivante, vous changez quelques lignes dans l’auditeur de création de vue et remplacez le contenu de **ColumnGuideAdornment.cs**.

  **Commandes**. Dans **Solution Explorer**, appuyez sur le bouton de pointeur droit sur le nœud de projet. Choisissez **l’ajouter &#124; nouvel article ...** commande pour ajouter un nouvel élément d’ornement de vue. Choisissez **Extensibility &#124; VSPackage** dans le volet de navigation gauche et choisissez **Custom Command** dans le volet droit. Entrez le nom **ColumnGuideCommands** comme nom de l’élément et choisissez **Ajouter**. En plus de plusieurs références, l’ajout des commandes et du paquet a également ajouté **ColumnGuideCommands.cs**, **ColumnGuideCommandsPackage.cs**, et **ColumnGuideCommandsPackage.vsct**. Dans la section suivante, vous remplacez le contenu des premiers et derniers fichiers pour définir et implémenter les commandes.

## <a name="set-up-the-text-view-creation-listener"></a>Configurez l’auditeur de création de vue de texte
Ouvrez *ColumnGuideAdornmentTextViewCreationListener.cs* dans l’éditeur. Ce code implémente un gestionnaire chaque fois que Visual Studio crée des vues de texte. Il y a des attributs qui contrôlent lorsque le gestionnaire est appelé en fonction des caractéristiques de la vue.

Le code doit également déclarer une couche d’ornement. Lorsque l’éditeur met à jour les vues, il obtient les couches d’ornement pour la vue et de ce qui obtient les éléments d’ornement. Vous pouvez déclarer la commande de votre couche par rapport à d’autres avec des attributs. Remplacer la ligne suivante :

```csharp
[Order(After = PredefinedAdornmentLayers.Caret)]
```

avec ces deux lignes:

```csharp
[Order(Before = PredefinedAdornmentLayers.Text)]
[TextViewRole(PredefinedTextViewRoles.Document)]
```

La ligne que vous avez remplacée est dans un groupe d’attributs qui déclarent une couche d’ornement. La première ligne que vous avez modifiée ne change que lorsque les lignes de guidage de colonne apparaissent. Tracer les lignes "avant" le texte dans la vue signifie qu’ils apparaissent derrière ou en dessous du texte. La deuxième ligne déclare que les ornements guide de colonne sont applicables aux entités de texte qui correspondent à votre notion d’un document, mais vous pouvez déclarer l’ornement, par exemple, pour fonctionner uniquement pour le texte modifiable. Il y a plus d’informations dans [le service de langue et les points d’extension de l’éditeur](../extensibility/language-service-and-editor-extension-points.md)

## <a name="implement-the-settings-manager"></a>Implémenter le gestionnaire des paramètres
Remplacer le contenu du *GuidesSettingsManager.cs* par le code suivant (expliqué ci-dessous):

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
                // Not present.  Allow user to remove the last column
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
        // can update.  We need nothing special in this event since the settings manager
        // is statically available.
        //
        internal delegate void SettingsChangedHandler();
        static internal event SettingsChangedHandler SettingsChanged;

    }
}

```

La plupart de ce code crée et analyse le\<format paramètres:\<"RGB (int\<>, int \<>, int>) int>, \<int>, ...".  Les entiers à la fin sont les colonnes à base unique où vous voulez des guides de colonne. L’extension des guides de colonne capture tous ses paramètres dans une seule chaîne de valeur de réglage.

Il ya quelques parties du code à mettre en évidence. La ligne de code suivante permet d’obtenir l’emballage géré Visual Studio pour le stockage des paramètres. Pour la plupart, cela abstrait sur le registre Windows, mais cette API est indépendante du mécanisme de stockage.

```csharp
internal static SettingsManager VsManagedSettingsManager =
    new ShellSettingsManager(ServiceProvider.GlobalProvider);
```

Le stockage des paramètres Visual Studio utilise un identifiant de catégorie et un identifiant de paramètre pour identifier uniquement tous les paramètres :

```csharp
private const string _collectionSettingsName = "Text Editor";
private const string _settingName = "Guides";
```

Vous n’avez `"Text Editor"` pas à utiliser comme nom de catégorie. Tu peux choisir ce que tu veux.

Les premières fonctions sont les points d’entrée pour modifier les paramètres. Ils vérifient les contraintes de haut niveau comme le nombre maximum de guides autorisés.  Ensuite, ils `WriteSettings`appellent , qui compose une `GuideLinesConfiguration`chaîne de réglages et définit la propriété . La configuration de cette propriété permet d’économiser `SettingsChanged` la valeur des `ColumnGuideAdornment` paramètres au magasin de paramètres Visual Studio et déclenche l’événement pour mettre à jour tous les objets, chacun associé à une vue textuelle.

Il ya un couple de fonctions `CanAddGuideline`de point d’entrée, tels que , qui sont utilisés pour implémenter des commandes qui changent les paramètres. Lorsque Visual Studio affiche des menus, il interroge les implémentations de commande pour voir si la commande est actuellement activée, quel est son nom, et ainsi de suite.  Ci-dessous vous voyez comment brancher ces points d’entrée pour les implémentations de commande. Pour plus d’informations sur les commandes, voir [Menus et commandes Extend](../extensibility/extending-menus-and-commands.md).

## <a name="implement-the-columnguideadornment-class"></a>Mettre en œuvre la classe ColumnGuideAdornment
La `ColumnGuideAdornment` classe est instantanée pour chaque vue de texte qui peut avoir des ornements. Cette classe est à l’écoute des événements sur les changements de vue ou les paramètres changeants, et les guides de colonne de mise à jour ou de redessinage si nécessaire.

Remplacer le contenu du *ColumnGuideAdornment.cs* par le code suivant (expliqué ci-dessous):

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

Les instances de cette <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> classe s’accrochent à l’associé et une liste d’objets `Line` dessinés sur la vue.

Le constructeur (appelé `ColumnGuideAdornmentTextViewCreationListener` à partir de quand Visual `Line` Studio crée de nouvelles vues) crée les objets de guidage de colonne.  Le constructeur ajoute également des `SettingsChanged` gestionnaires pour `GuidesSettingsManager`l’événement `LayoutChanged` (défini dans ) et les événements de vue et `Closed`.

L’événement `LayoutChanged` s’allume en raison de plusieurs types de changements dans la vue, y compris lorsque Visual Studio crée la vue. Le `OnViewLayoutChanged` gestionnaire `AddGuidelinesToAdornmentLayer` appelle à exécuter. Le code `OnViewLayoutChanged` détermine s’il doit mettre à jour les positions de ligne en fonction de modifications telles que les modifications de la taille des polices, les gouttières, le défilement horizontal, etc. Le code `UpdatePositions` dans les causes des lignes de guidage à dessiner entre les caractères ou juste après la colonne de texte qui est dans le caractère spécifié compensé dans la ligne de texte.

Chaque fois `SettingsChanged` que les paramètres `Line` changent la fonction recrée juste tous les objets avec quels que soient les nouveaux paramètres. Après avoir défini les positions de `Line` ligne, `ColumnGuideAdornment` le code supprime tous les objets précédents de la couche d’ornement et en ajoute les nouveaux.

## <a name="define-the-commands-menus-and-menu-placements"></a>Définissez les commandes, les menus et les emplacements de menu
Il peut y avoir beaucoup à déclarer des commandes et des menus, placer des groupes de commandes ou des menus sur divers autres menus, et brancher les gestionnaires de commande. Cette procédure pas à pas met en évidence le fonctionnement des commandes dans cette extension, mais pour des informations plus [approfondies,](../extensibility/extending-menus-and-commands.md)voir Extend menus et commandes .

### <a name="introduction-to-the-code"></a>Introduction au code
L’extension des Guides de colonne montre la déclaration d’un groupe de commandes qui appartiennent ensemble (ajouter la colonne, supprimer la colonne, changer la couleur de la ligne), puis placer ce groupe sur un sous-menu du menu contextuelle de l’éditeur.  L’extension des Guides de colonne ajoute également les commandes au menu **Principal Edit,** mais les garde invisibles, discutés comme un modèle commun ci-dessous.

Il y a trois parties à la mise en œuvre des commandes : ColumnGuideCommandsPackage.cs, ColumnGuideCommandsPackage.vsct, et ColumnGuideCommands.cs. Le code généré par les modèles met une commande sur le menu **Tools** qui apparaît une boîte de dialogue comme l’implémentation. Vous pouvez regarder comment cela est mis en œuvre dans les fichiers *.vsct* et *ColumnGuideCommands.cs* car il est simple. Vous remplacez le code dans ces fichiers ci-dessous.

Le code de paquet contient des déclarations de plaque chauffante nécessaires pour Visual Studio pour découvrir que l’extension offre des commandes et pour trouver où placer les commandes. Lorsque le paquet est paralé, il instantanéise la classe de mise en œuvre des commandes. Pour plus d’informations sur les forfaits relatifs aux commandes, voir [Les menus et les commandes Extend](../extensibility/extending-menus-and-commands.md).

### <a name="a-common-commands-pattern"></a>Un modèle de commande commun
Les commandes dans l’extension des Guides de colonnes sont un exemple d’un modèle très commun dans Visual Studio. Vous mettez des commandes connexes dans un groupe, et vous mettez`<CommandFlag>CommandWellOnly</CommandFlag>`ce groupe sur un menu principal, souvent avec " mis à rendre la commande invisible.  Mettre des commandes sur les menus principaux (tels que **Edit**) leur donne de beaux noms (tels que **Edit.AddColumnGuide**), qui sont utiles pour trouver des commandes lors de la réaffectation des liaisons clés dans **Tools Options**. Il est également utile pour obtenir l’achèvement lors de l’invocation des commandes de la fenêtre de **commandement**.

Vous ajoutez ensuite le groupe de commandes aux menus contextuels ou sous-menus où vous vous attendez à ce que l’utilisateur utilise les commandes. Visual Studio `CommandWellOnly` se traite comme un drapeau d’invisibilité pour les menus principaux seulement. Lorsque vous placez le même groupe de commandes sur un menu contextuelle ou un sous-menu, les commandes sont visibles.

Dans le cadre du modèle commun, l’extension des Guides de colonnes crée un deuxième groupe qui contient un seul sous-menu. Le sous-menu contient à son tour le premier groupe avec les commandes de guide à quatre colonnes. Le deuxième groupe qui détient le sous-menu est l’actif réutilisable que vous placez sur différents menus contextuels, qui met un sous-menu sur ces menus contextuels.

### <a name="the-vsct-file"></a>Le fichier .vsct
Le fichier *.vsct* déclare les commandes et où ils vont, avec des icônes et ainsi de suite. Remplacer le contenu du fichier *.vsct* par le code suivant (expliqué ci-dessous):

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

**GUIDS**. Pour Visual Studio pour trouver vos gestionnaires de commande et les invoquer, vous devez vous assurer que le paquet GUID déclaré dans le fichier *ColumnGuideCommandsPackage.cs* (généré à partir du modèle d’élément de projet) correspond au paquet GUID déclaré dans le fichier *.vsct* (copié d’en haut). Si vous réutilisationz ce code d’échantillon, vous devez vous assurer d’avoir un GUID différent afin de ne pas entrer en conflit avec quelqu’un d’autre qui peut avoir copié ce code.

Trouvez cette ligne dans *ColumnGuideCommandsPackage.cs* et copiez le GUID entre les guillemets :

```csharp
public const string PackageGuidString = "ef726849-5447-4f73-8de5-01b9e930f7cd";
```

Ensuite, collez le GUID dans le fichier *.vsct* afin `Symbols` d’avoir la ligne suivante dans vos déclarations:

```xml
<GuidSymbol name="guidColumnGuideCommandsPkg"
            value="{ef726849-5447-4f73-8de5-01b9e930f7cd}" />
```

Les GUIDs pour l’ensemble de commande et le fichier d’image bitmap doivent être uniques pour vos extensions, aussi:

```xml
<GuidSymbol name="guidColumnGuidesCommandSet"
            value="{c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e}">
<GuidSymbol name="guidImages" value="{2C99F852-587C-43AF-AA2D-F605DE2E46EF}">
```

Mais, vous n’avez pas besoin de changer l’ensemble de commande et les GUIDs image bitmap dans cette procédure pas à pas pour obtenir le code de fonctionner. Le défini de commande GUID doit correspondre à la déclaration dans le fichier *ColumnGuideCommands.cs,* mais vous remplacez le contenu de ce fichier, aussi; par conséquent, les GUIDs correspondront.

D’autres GUID dans le fichier *.vsct* identifient les menus préexistants auxquels les commandes de guide de colonne sont ajoutées, de sorte qu’elles ne changent jamais.

**Sections de fichiers**. Le *.vsct* a trois sections extérieures: commandes, placements et symboles. La section commandes définit les groupes de commande, les menus, les boutons ou les éléments de menu, et les bitmaps pour les icônes. La section placements déclare où les groupes vont sur les menus ou les placements supplémentaires sur les menus préexistants. La section des symboles déclare les identifiants utilisés ailleurs dans le fichier *.vsct,* ce qui rend le code *.vsct* plus lisible que d’avoir des GUIDs et des numéros hex partout.

**Section des commandes, définitions des groupes**. La section des commandes définit d’abord les groupes de commandement. Les groupes de commandes sont des commandes que vous voyez dans les menus avec de légères lignes grises séparant les groupes. Un groupe peut également remplir un sous-menu entier, comme dans cet exemple, et vous ne voyez pas les lignes de séparation grises dans ce cas. Les fichiers *.vsct* déclarent `GuidesMenuItemsGroup` deux groupes, `IDM_VS_MENU_EDIT` le qui est parenté `GuidesContextMenuGroup` à la (le menu **principal Edit)** et le qui est parent à la `IDM_VS_CTXT_CODEWIN` (menu contexte de l’éditeur de code).

La deuxième déclaration `0x0600` de groupe a une priorité :

```xml
<Group guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
             priority="0x0600">
```

L’idée est de mettre le sous-menu des guides de colonne à la fin de n’importe quel menu contextuelle auquel vous ajoutez le groupe de sous-menu. Mais, vous ne devriez pas supposer que vous savez mieux et forcer `0xFFFF`le sous-menu à toujours être le dernier en utilisant une priorité de . Vous devez expérimenter avec le numéro pour voir où se trouve votre sous-menu sur les menus contextuels où vous le placez. Dans ce `0x0600` cas, est assez élevé pour le mettre à la fin des menus autant que vous pouvez voir, mais il laisse place à quelqu’un d’autre pour concevoir leur extension pour être inférieur à l’extension des guides de colonne si c’est souhaitable.

**Section commandes, définition du menu**. Ensuite, la section de commande `GuidesSubMenu`définit le `GuidesContextMenuGroup`sous-menu , parenté à la . Le `GuidesContextMenuGroup` groupe que vous ajoutez à tous les menus de contexte pertinents. Dans la section placements, le code place le groupe avec les commandes de guide à quatre colonnes sur ce sous-menu.

**Section commandes, définitions de boutons**. La section commandes définit ensuite les éléments de menu ou les boutons qui sont les commandes de guides à quatre colonnes. `CommandWellOnly`, discuté ci-dessus, signifie que les commandes sont invisibles lorsqu’elles sont placées sur un menu principal. Deux des déclarations de bouton d’élément de menu `AllowParams` (ajouter le guide et supprimer le guide) ont également un drapeau :

```xml
<CommandFlag>AllowParams</CommandFlag>
```

Ce drapeau permet, en plus d’avoir des emplacements de menu principal, la commande de recevoir des arguments lorsque Visual Studio invoque le gestionnaire de commande.  Si l’utilisateur exécute la commande à partir de la fenêtre de commande, l’argument est transmis au gestionnaire de commande dans les arguments de l’événement.

**Sections de commande, définitions de bitmaps**. Enfin, la section commandes déclare les bitmaps ou les icônes utilisées pour les commandes. Cette section est une déclaration simple qui identifie la ressource du projet et répertorie les index à une base des icônes utilisées. La section symboles du fichier *.vsct* déclare les valeurs des identificateurs utilisés comme index. Cette procédure pas à pas utilise la bande de bitmap fournie avec le modèle d’élément de commande personnalisé ajouté au projet.

**Section Placements**. Après la section des commandes est la section de placements. Le premier est l’endroit où le code ajoute le premier groupe discuté ci-dessus qui détient les commandes de guide à quatre colonnes au sous-menu où les commandes apparaissent:

```xml
<CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
                  priority="0x0100">
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" />
</CommandPlacement>
```

Tous les autres placements `GuidesContextMenuGroup` ajoutent le `GuidesSubMenu`(qui contient le ) à d’autres menus de contexte d’éditeur. Lorsque le code `GuidesContextMenuGroup`a déclaré le , il a été parenté au menu de contexte de l’éditeur de code. C’est pourquoi vous ne voyez pas de placement pour le menu contextuelle de l’éditeur de code.

**Section symboles**. Comme indiqué ci-dessus, la section des symboles déclare les identificateurs utilisés ailleurs dans le fichier *.vsct,* ce qui rend le code *.vsct* plus lisible que d’avoir des GUIDs et des numéros hex partout. Les points importants de cette section sont que le paquet GUID doit être d’accord avec la déclaration dans la catégorie des paquets. Et, le jeu de commande GUID doit être d’accord avec la déclaration dans la classe de mise en œuvre de commande.

## <a name="implement-the-commands"></a>Mettre en œuvre les commandes
Le *fichier ColumnGuideCommands.cs* implémente les commandes et connecte les gestionnaires. Lorsque Visual Studio charge le paquet et l’initialise, le paquet fait à son tour appel `Initialize` à la classe de mise en œuvre des commandes. L’initialisation des commandes n’a qu’instantanéise la classe, et le constructeur branche tous les maîtres de commande.

Remplacer le contenu du *fichier ColumnGuideCommands.cs* par le code suivant (expliqué ci-dessous) :

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

**Correction des références**. Vous manquez une référence à ce stade. Appuyez sur le bouton pointeur droit sur le nœud Références dans la Solution Explorer. Choisissez la commande **Add ....** Le dialogue **Add Reference** dispose d’une boîte de recherche dans le coin supérieur droit. Entrez "éditeur" (sans les citations doubles). Choisissez l’élément **Microsoft.VisualStudio.Editor** (vous devez cocher la case à gauche de l’élément, pas seulement sélectionner l’élément) et choisissez **OK** pour ajouter la référence.

**Initialisation**.  Lorsque la classe de paquets `Initialize` est initiale, elle fait appel à la classe de mise en œuvre des commandes. L’initialisation `ColumnGuideCommands` permet d’instantanéiser la classe et d’économiser l’instance de classe et la référence du paquet chez les membres de la classe.

Examinons l’un des raccordements de gestionnaire de commande du constructeur de classe :

```csharp
_addGuidelineCommand =
    new OleMenuCommand(AddColumnGuideExecuted, null,
                       AddColumnGuideBeforeQueryStatus,
                       new CommandID(ColumnGuideCommands.CommandSet,
                                     cmdidAddColumnGuide));

```

Vous créez `OleMenuCommand`un . Visual Studio utilise le système de commande Microsoft Office. Les arguments clés lors `OleMenuCommand` de l’instantanéise d’un est la fonction qui implémente la commande (`AddColumnGuideExecuted`), la fonction à appeler lorsque Visual Studio affiche un menu avec la commande (`AddColumnGuideBeforeQueryStatus`), et l’ID de commande. Le studio visuel appelle la fonction de statut de requête avant d’afficher une commande sur un menu de sorte que la commande puisse se rendre invisible ou grisé dehors pour un affichage particulier du menu (par exemple, désactivant **la copie** s’il n’y a pas de sélection), changez son icône, ou même changez son nom (par exemple, d’ajouter quelque chose à enlever quelque chose), et ainsi de suite. L’ID de commande doit correspondre à une pièce d’identité de commande déclarée dans le fichier *.vsct.* Les chaînes pour l’ensemble de commande et les guides de colonne ajoutent la commande doit correspondre entre le fichier *.vsct* et le *ColumnGuideCommands.cs*.

La ligne suivante fournit une assistance pour quand les utilisateurs invoquent la commande via la fenêtre de commande (expliquée ci-dessous) :

```csharp
_addGuidelineCommand.ParametersDescription = "<column>";
```

 **Statut de requête**. L’état de `AddColumnGuideBeforeQueryStatus` la `RemoveColumnGuideBeforeQueryStatus` requête fonctionne et vérifie certains paramètres (comme le nombre maximum de guides ou de colonnes max) ou s’il y a un guide de colonne à supprimer. Ils permettent les commandes si les conditions sont bonnes.  Les fonctions d’état de requête doivent être efficaces parce qu’elles s’exécutent chaque fois que Visual Studio affiche un menu et pour chaque commande sur le menu.

 **Fonction AddColumnGuideExecuted**. La partie intéressante de l’ajout d’un guide est de comprendre la vue actuelle de l’éditeur et l’emplacement caret.  Tout d’abord, cette fonction appelle `GetApplicableColumn`, qui vérifie s’il ya un argument fourni par l’utilisateur dans les arguments de l’événement du gestionnaire de commande, et s’il n’y en a pas, la fonction vérifie le point de vue de l’éditeur:

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

`GetCurrentEditorColumn`doit creuser un peu <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> pour obtenir une vue du code.  Si vous `GetActiveTextView`tracez à travers , `GetActiveView`, et `GetTextViewFromVsTextView`, vous pouvez voir comment le faire. Le code suivant est le code pertinent abstrait, en commençant par la sélection actuelle, puis obtenir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>le cadre <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> de la sélection, puis obtenir docView du cadre comme un , puis obtenir un de l’IVsTextView, puis obtenir un hôte de vue, et enfin l’IWpfTextView:

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

Une fois que vous avez un IWpfTextView, vous pouvez obtenir la colonne où le caret est situé:

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

Avec la colonne actuelle en main où l’utilisateur a cliqué, le code appelle simplement le gestionnaire de paramètres pour ajouter ou supprimer la colonne. Le gestionnaire des paramètres déclenche `ColumnGuideAdornment` l’événement auquel tous les objets écoutent. Lorsque l’événement s’allume, ces objets mettent à jour leurs vues de texte associées avec de nouveaux paramètres de guide de colonne.

## <a name="invoke-command-from-the-command-window"></a>Invoquer le commandement de la fenêtre de commandement
L’échantillon de guides de colonne permet aux utilisateurs d’invoquer deux commandes de la fenêtre de commande comme une forme d’extéabilité. Si vous utilisez la **vue &#124; d’autres** windows &#124; commande de fenêtre de commande, vous pouvez voir la fenêtre de commande. Vous pouvez interagir avec la fenêtre de commande en entrant « modifier », et avec l’achèvement du nom de commande et en fournissant l’argument 120, vous avez le résultat suivant :

```csharp
> Edit.AddColumnGuide 120
>
```

Les pièces de l’échantillon qui permettent ce comportement sont `ColumnGuideCommands` dans les déclarations de fichiers *.vsct,* le constructeur de classe quand il accroche les gestionnaires de commande, et les implémentations de gestionnaire de commande qui vérifient les arguments d’événement.

Vous avez`<CommandFlag>CommandWellOnly</CommandFlag>`vu " dans le fichier *.vsct* ainsi que les placements dans le menu principal **Edit,** même si les commandes ne sont pas affichées dans **l’interface** utilisateur du menu Edit. Les avoir sur le menu **Principal Edit** leur donne des noms comme **Edit.AddColumnGuide**. La déclaration de groupe de commandes qui détient les quatre commandes a placé le groupe sur le menu **Edit** directement :

```xml
<Group guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
             priority="0xB801">
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_EDIT" />
      </Group>

```

La section des boutons a `CommandWellOnly` déclaré plus tard les commandes de `AllowParams`les garder invisibles sur le menu principal et les a déclarés avec :

```xml
<Button guid="guidColumnGuidesCommandSet" id="cmdidAddColumnGuide"
        priority="0x0100" type="Button">
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
  <Icon guid="guidImages" id="bmpPicAddGuide" />
  <CommandFlag>CommandWellOnly</CommandFlag>
  <CommandFlag>AllowParams</CommandFlag>

```

Vous avez vu le gestionnaire `ColumnGuideCommands` de commande brancher le code dans le constructeur de classe a fourni une description du paramètre autorisé :

```csharp
_addGuidelineCommand.ParametersDescription = "<column>";

```

Vous avez `GetApplicableColumn` vu `OleMenuCmdEventArgs` les vérifications de fonction pour une valeur avant de vérifier la vue de l’éditeur pour une colonne en cours:

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

## <a name="try-your-extension"></a>Essayez votre extension
Vous pouvez maintenant appuyer sur **F5** pour exécuter votre extension De guides de colonnes. Ouvrez un fichier texte et utilisez le menu contextuel de l’éditeur pour ajouter des lignes de guidage, les supprimer et changer de couleur. Cliquez sur le texte (pas l’espace blanc passé la fin de la ligne) pour ajouter un guide de colonne, ou l’éditeur l’ajoute à la dernière colonne sur la ligne. Si vous utilisez la fenêtre de commande et invoquez les commandes avec un argument, vous pouvez ajouter des guides de colonne n’importe où.

Si vous voulez essayer différents placements de commande, changer de nom, changer d’icônes, et ainsi de suite, et vous avez des problèmes avec Visual Studio vous montrant le dernier code dans les menus, vous pouvez réinitialiser la ruche expérimentale dans laquelle vous débogage. Apportez le **menu Windows Start** et tapez "reset". Rechercher et exécuter la commande, **Réinitialiser la prochaine instance expérimentale Visual Studio**. Cette commande nettoie la ruche expérimentale de registre de tous les composants d’extension. Il ne nettoie pas les paramètres à partir de composants, de sorte que tous les guides que vous aviez lorsque vous arrêtez la ruche expérimentale de Visual Studio sont toujours là lorsque votre code lit le magasin des paramètres sur le lancement prochain.

## <a name="finished-code-project"></a>Projet de code fini
Il y aura bientôt un projet GitHub d’échantillons visual Studio Extensibility, et le projet terminé sera là. Cet article sera mis à jour pour indiquer quand cela se produit. Le projet d’échantillon terminé peut avoir des guids différents et aura une bande de bitmaps différente pour les icônes de commande.

Vous pouvez essayer une version de la fonction guides de colonne avec cette[extension](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.EditorGuidelines)Visual Studio Gallery .

## <a name="see-also"></a>Voir aussi
- [À l’intérieur de l’éditeur](../extensibility/inside-the-editor.md)
- [Étendre les services d’éditeur et de langue](../extensibility/extending-the-editor-and-language-services.md)
- [Service linguistique et points d’extension de l’éditeur](../extensibility/language-service-and-editor-extension-points.md)
- [Étendre les menus et les commandes](../extensibility/extending-menus-and-commands.md)
- [Ajouter un sous-mois à un menu](../extensibility/adding-a-submenu-to-a-menu.md)
- [Créez une extension avec un modèle d’élément d’éditeur](../extensibility/creating-an-extension-with-an-editor-item-template.md)
