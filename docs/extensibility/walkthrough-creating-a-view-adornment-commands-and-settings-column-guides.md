---
title: "Création d’un ornement de vue, les commandes et paramètres | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4a2df0a3-42da-4f7b-996f-ee16a35ac922
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: c1836489b1845bca9e57daf83fc97bafeaf9da72
ms.contentlocale: fr-fr
ms.lasthandoff: 09/06/2017

---
# <a name="walkthrough-creating-a-view-adornment-commands-and-settings-column-guides"></a>Procédure pas à pas : Création d’un ornement de vue, les commandes et les paramètres (repères de colonne)
Vous pouvez étendre l’éditeur de texte/code de Visual Studio avec les commandes et les effets de la vue.  Cette rubrique montre comment démarrer avec une fonctionnalité d’extension populaires, repères de colonne.  Repères de colonne sont visuellement clair lignes dessinées sur la vue de l’éditeur de texte pour vous aider à gérer votre code pour les largeurs de colonne spécifique.  Code de mise en forme en particulier peut être important pour obtenir des exemples vous incluez dans les documents, des billets de blog, ou les rapports de bogues.  
  
 Dans cette procédure pas à pas, vous allez :  
  
-   Créez un projet VSIX  
  
-   Ajouter un ornement de vue de l’éditeur  
  
-   Ajouter la prise en charge pour l’enregistrement et l’obtention des paramètres (où pour dessiner les repères de colonne et leur couleur)  
  
-   Ajouter des commandes (Ajouter/supprimer des repères de colonne, modifier leur couleur)  
  
-   Placez les commandes du menu Edition et les menus contextuels de document texte  
  
-   Ajouter la prise en charge pour appeler les commandes à partir de la fenêtre de commande Visual Studio  
  
 Vous pouvez essayer une version de la fonctionnalité de repères de colonne avec cette galerie Visual Studio[extension](https://visualstudiogallery.msdn.microsoft.com/da227a0b-0e31-4a11-8f6b-3a149cf2e459?SRC=Home).  
  
 **Remarque**: dans cette procédure pas à pas, vous collez beaucoup de code dans quelques fichiers générés par les modèles d’extension visual studio, mais dès cette procédure pas à pas fait référence à une solution terminée sur github avec d’autres exemples d’extension.  Le code complet est légèrement différent dans la mesure où il a des icônes de commande réel au lieu d’utiliser des icônes de generictemplate.  
  
## <a name="getting-started"></a>Commencer  
 À partir de Visual Studio 2015, vous n’installez pas le Kit de développement logiciel Visual Studio à partir du centre de téléchargement. Il est inclus comme une fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit SDK VS ultérieurement. Pour plus d’informations, consultez [l’installation de Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="setting-up-the-solution"></a>Configuration de la Solution  
 Tout d’abord vous créez un projet VSIX, ajoutez un ornement de vue de l’éditeur et puis ajoutez une commande (qui ajoute un VSPackage doit détenir la commande).  L’architecture de base est la suivante :  
  
-   Vous disposez d’un écouteur de la création de vue de texte qui crée un `ColumnGuideAdornment` objet par la vue.  Cet objet est à l’écoute des événements sur la modification de la vue ou les repères de colonne mise à jour ou écran Paramètres de modification, si nécessaire.  
  
-   Il existe un `GuidesSettingsManager` qui gère la lecture et en écriture à partir du stockage de paramètres de Visual Studio.  Le Gestionnaire de paramètres a également les opérations de mise à jour les paramètres qui prennent en charge les commandes de l’utilisateur (ajouter une colonne, supprimez la colonne, modifier la couleur).  
  
-   Il existe un package VSIP qui est nécessaire si vous avez des commandes de l’utilisateur, mais il est simplement un code réutilisable qui initialise l’objet d’implémentation de commandes.  
  
-   Il existe un `ColumnGuideCommands` objet qui implémente les commandes de l’utilisateur et le raccorde les gestionnaires de commandes pour les commandes déclaré dans le fichier .vsct.  
  
 **VSIX**.  Utilisez **fichier &#124; Nouveau...**  commande pour créer un projet.  Choisissez le nœud d’extensibilité sous c# dans le volet de navigation gauche, **projet VSIX** dans le volet droit.  Entrez le nom ColumnGuides et choisissez **OK** pour créer le projet.  
  
 **Afficher les ornements**.  Appuyez sur le bouton droit du pointeur sur le nœud de projet dans l’Explorateur de solutions.  Choisissez le **ajouter &#124; Nouvel élément...**  commande pour ajouter un nouvel élément d’ornement de vue.  Choisissez **extensibilité &#124; Éditeur de** dans le volet de navigation gauche, choisissez **ornement de la fenêtre d’affichage de l’éditeur** dans le volet droit.  Entrez le nom ColumnGuideAdornment comme nom d’élément et choisissez **ajouter** pour l’ajouter.  
  
 Vous pouvez voir ce modèle d’élément ajouté deux fichiers au projet (ainsi que les références et ainsi de suite) : ColumnGuideAdornment.cs et ColumnGuideAdornmentTextViewCreationListener.cs.  Les modèles de dessiner uniquement un rectangle violet sur la vue.  Ci-dessous vous modifier quelques lignes dans l’écouteur de la création de vue et remplacez le contenu de ColumnGuideAdornment.cs.  
  
 **Commandes**.  Appuyez sur le bouton droit du pointeur sur le nœud de projet dans l’Explorateur de solutions.  Choisissez le **ajouter &#124; Nouvel élément...**  commande pour ajouter un nouvel élément d’ornement de vue.  Choisissez **extensibilité &#124; VSPackage** dans le volet de navigation gauche, choisissez **commande personnalisée** dans le volet droit.  Entrez le nom ColumnGuideCommands comme nom d’élément et choisissez **ajouter** pour l’ajouter.  En plus de plusieurs références, ajouter les commandes et les package ajouté ColumnGuideCommands.cs, ColumnGuideCommandsPackage.cs et ColumnGuideCommandsPackage.vsct.  Ci-dessous, vous allez remplacer le contenu des premier et derniers fichiers pour définir et implémenter les commandes.  
  
## <a name="setting-up-the-text-view-creation-listener"></a>Configuration de l’écouteur de la création de vue de texte  
 Ouvrez ColumnGuideAdornmentTextViewCreationListener.cs dans l’éditeur.  Ce code implémente un gestionnaire pour chaque fois que Visual Studio crée des affichages de texte.  Il existe des attributs qui contrôlent lorsque le gestionnaire est appelé en fonction des caractéristiques de la vue.  
  
 Le code doit également déclarer d’une couche d’ornement.  Lorsque l’éditeur de vues de mises à jour, il obtient les couches d’ornement pour l’affichage et à partir de qui obtient les éléments d’ornement.  Vous pouvez déclarer l’ordre de votre couche par rapport à d’autres attributs.  Remplacez la ligne suivante :  
  
```csharp  
[Order(After = PredefinedAdornmentLayers.Caret)]  
```  
  
 avec ces deux lignes :  
  
```csharp  
[Order(Before = PredefinedAdornmentLayers.Text)]  
[TextViewRole(PredefinedTextViewRoles.Document)]  
```  
  
 La ligne que vous avez remplacé est dans un groupe d’attributs qui déclarent une couche d’ornement.   La première ligne que vous avez modifié dans lequel les lignes de repère de colonne s’affichent uniquement les modifications.  Dessine les lignes « avant » le texte dans la vue signifie qu’ils apparaissent derrière ou au-dessous du texte.  La deuxième ligne déclare que les ornements de guide de colonne sont applicables aux entités de texte qui correspondent à votre notion d’un document, mais vous pouvez déclarer l’ornement, par exemple, pour seulement le travail pour le texte modifiable.  Il existe plus d’informations dans [Service de langage et les Points d’Extension de l’éditeur](../extensibility/language-service-and-editor-extension-points.md)  
  
## <a name="implementing-the-settings-manager"></a>Implémentation du Gestionnaire de paramètres  
 Remplacez le contenu de la GuidesSettingsManager.cs par le code suivant (voir ci-après) :  
  
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
  
 La majeure partie de ce code crée simplement et analyse le format de paramètres : « RVB (\<int >,\<int >,\<int >) \<int >, \<int >,... ».  Les entiers à la fin sont les colonnes de base un où vous souhaitez les repères de colonne.  L’extension de repères de colonne capture tous ses paramètres dans une chaîne de valeur de paramètre unique.  
  
 Il existe certaines parties du code intéressant.  La ligne de code suivante obtient le wrapper managé Visual Studio pour le stockage des paramètres.  Dans la plupart des cas, Ceci extrait sur le Registre Windows, mais cette API méthode est indépendante du mécanisme de stockage.  
  
```csharp  
internal static SettingsManager VsManagedSettingsManager =  
    new ShellSettingsManager(ServiceProvider.GlobalProvider);  
```  
  
 Le stockage des paramètres Visual Studio utilise un identificateur de catégorie et un identificateur de paramètre pour identifier tous les paramètres :  
  
```csharp  
private const string _collectionSettingsName = "Text Editor";  
private const string _settingName = "Guides";  
```  
  
 Vous n’avez pas à utiliser `"Text Editor"` comme catégorie de nom et vous pouvez choisir comme vous le souhaitez.  
  
 Les premières fonctions peu sont les points d’entrée pour modifier les paramètres.  Ils vérifient comme nombre maximal autorisé de repères de contraintes de haut niveau.  Ensuite, elles appellent `WriteSettings` qui compose une chaîne de paramètres et définit la propriété `GuideLinesConfiguration`.  Définition de cette propriété enregistre les valeurs des paramètres pour le stockage de paramètres de Visual Studio et se déclenche le `SettingsChanged` pour mettre à jour tous les événements le `ColumnGuideAdornment` d’objets, chacun étant associé à une vue de texte.  
  
 Il existe quelques fonctions de point d’entrée, tels que `CanAddGuideline`, qui permettent d’implémenter des commandes qui modifient les paramètres.  Lorsque Visual Studio affiche des menus, il interroge les implémentations de commande pour voir si la commande est actuellement activée, ce qui est son nom, etc..  Ci-dessous, vous verrez comment connecter ces points d’entrée pour les implémentations de la commande.  Consultez [étendant les Menus et commandes](../extensibility/extending-menus-and-commands.md) pour plus d’informations sur les commandes.  
  
## <a name="implementing-the-columnguideadornment-class"></a>Implémentation de la classe ColumnGuideAdornment  
 La `ColumnGuideAdornment` classe est instanciée pour chaque vue de texte qui peut avoir des ornements.  Cette classe est à l’écoute des événements sur la modification de la vue ou les repères de colonne mise à jour ou écran Paramètres de modification, si nécessaire.  
  
 Remplacez le contenu de la ColumnGuideAdornment.cs par le code suivant (voir ci-après) :  
  
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
  
 Les instances de cette classe contiennent associé <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> et une liste de `Line` dessinées sur la vue des objets.  
  
 Le constructeur (appelée à partir de `ColumnGuideAdornmentTextViewCreationListener` lorsque Visual Studio crée des nouvelles vues) crée le repère de colonne `Line` objets.  Le constructeur ajoute également des gestionnaires pour les `SettingsChanged` événement (défini dans `GuidesSettingsManager`) et les événements d’affichage `LayoutChanged` et `Closed`.  
  
 Le `LayoutChanged` se déclenche des événements en raison de plusieurs types de modifications dans la vue, y compris lorsque Visual Studio crée la vue.  Le `OnViewLayoutChanged` appels du Gestionnaire de `AddGuidelinesToAdornmentLayer` à exécuter.  Le code dans `OnViewLayoutChanged` détermine s’il faut mettre à jour les positions de ligne en fonction des modifications telles que les modifications de taille de police, espacement de la vue, un défilement horizontal et ainsi de suite.  Le code dans `UpdatePositions` provoque des lignes de repère dessiner entre caractères ou juste après la colonne de texte qui se trouve dans le décalage de caractère spécifiée dans la ligne de texte.  
  
 Chaque fois que les paramètres changent le `SettingsChanged` fonction recrée simplement tous le `Line` objets avec les nouveaux paramètres sont.  Après avoir défini les positions de ligne, le code supprime toutes les précédentes `Line` des objets de la `ColumnGuideAdornment` couche d’ornement et ajoute les nouveaux.  
  
## <a name="defining-the-commands-menus-and-menu-placements"></a>Définition des commandes, des Menus et des emplacements de Menu  
 Il peut y avoir beaucoup à déclarer les menus et commandes, placer des groupes de commandes ou de menus sur divers autres menus et raccorder les gestionnaires de commandes.  Cette procédure pas à pas met en évidence le fonctionnement des commandes de cette extension, mais pour plus d’informations, consultez [étendant les Menus et commandes](../extensibility/extending-menus-and-commands.md).  
  
### <a name="introduction-to-the-code"></a>Introduction au Code  
 L’extension de repères de colonne illustre la déclaration d’un groupe de commandes qui vont ensemble (ajouter une colonne, supprimez la colonne, modifier la couleur de ligne) et ensuite placer ce groupe sur un sous-menu du menu contextuel de l’éditeur.  L’extension de repères de colonne ajoute également les commandes de la main **modifier** menu, mais conserve les invisibles, présentés comme un modèle commun ci-dessous.  
  
 Il existe trois parties à l’implémentation de commandes : ColumnGuideCommandsPackage.cs, ColumnGuideCommandsPackage.vsct et ColumnGuideCommands.cs.  Le code généré par les modèles de place une commande le **outils** menu qui s’affiche une boîte de dialogue que l’implémentation.  Vous pouvez examiner comment qui est implémenté dans les fichiers de ColumnGuideCommands.cs et de .vsct, car il est assez simple.  Vous allez remplacer le code dans ces fichiers ci-dessous.  
  
 Le code du package est déclarations réutilisable qui sont requises pour Visual Studio de découvrir que l’extension offre les commandes et où placer les commandes.  Lorsque le package s’initialise, il instancier la classe d’implémentation de commandes.  Consultez les commandes de liens ci-dessus pour plus d’informations sur les packages de commandes.  
  
### <a name="a-common-commands-pattern"></a>Un modèle commun de commandes  
 Les commandes dans l’extension de repères de colonne sont un exemple d’un modèle très courant dans Visual Studio.  Vous placez des commandes associées dans un groupe, et vous placez ce groupe dans un menu principal, souvent avec «`<CommandFlag>CommandWellOnly</CommandFlag>`» définie pour rendre la commande invisible.  Placer des commandes dans les menus principaux (tel que **modifier**) ainsi leur donne la personnalisation des noms (tel que **Edit.AddColumnGuide**) qui sont utile pour identifier les commandes lors de l’affectation des combinaisons de touches dans  **Options des outils** et pour l’obtention de saisie semi-automatique lors de l’appel des commandes à partir de la **fenêtre commande**.  
  
 Vous pouvez ensuite ajouter le groupe de commandes aux menus contextuels ou sub à l’emplacement prévu utilisateur à utiliser les commandes de menus.  Visual Studio traite `CommandWellOnly` comme un indicateur d’invisibilité est passée pour les menus principaux uniquement.  Lorsque vous placez le même groupe de commandes sur un menu contextuel ou sub, les commandes sont visibles.  
  
 Dans le cadre du modèle commun, l’extension de repères de colonne crée un deuxième groupe qui contient un sous-menu unique.  Le sous-menu contient à son tour le premier groupe avec les commandes de guide de quatre colonnes.  Le deuxième groupe qui contient le sous-menu est la ressource réutilisable que vous placez dans les différents menus contextuels, qui met un sous-menu dans les menus contextuels.  
  
### <a name="the-vsct-file"></a>Le fichier .vsct  
 Le fichier .vsct déclare les commandes et son accès, ainsi que des icônes et ainsi de suite.  Remplacez le contenu du fichier .vsct par le code suivant (voir ci-après) :  
  
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
  
 **GUID**.  Pour Visual Studio rechercher vos gestionnaires de commandes et de les appeler, vous devez vous assurer le package que GUID déclaré dans le fichier ColumnGuideCommandsPackage.cs (généré à partir du modèle d’élément de projet) correspond au package que GUID déclaré dans le fichier .vsct (copié à partir du haut ).  Si vous réutilisez cet exemple de code, il se peut que vous devez vous assurer que vous avez un autre GUID afin que vous ne sont pas en conflit avec toute personne peut avoir copié ce code.  
  
 Rechercher cette ligne dans ColumnGuideCommandsPackage.cs et copiez le GUID entre des guillemets simples :  
  
```csharp  
public const string PackageGuidString = "ef726849-5447-4f73-8de5-01b9e930f7cd";  
```  
  
 Puis collez le GUID dans le fichier .vsct, afin que vous ayez la ligne suivante votre `Symbols` déclarations :  
  
```xml  
<GuidSymbol name="guidColumnGuideCommandsPkg"   
            value="{ef726849-5447-4f73-8de5-01b9e930f7cd}" />  
```  
  
 Les GUID de la commande est défini et le fichier d’image bitmap doit être unique pour vos extensions trop :  
  
```xml  
<GuidSymbol name="guidColumnGuidesCommandSet"   
            value="{c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e}">  
<GuidSymbol name="guidImages" value="{2C99F852-587C-43AF-AA2D-F605DE2E46EF}">  
```  
  
 Toutefois, vous n’avez pas besoin modifier le jeu de commandes et de bitmap GUID d’image dans cette procédure pas à pas pour obtenir le code fonctionne.  La commande de définir le GUID doit correspondre à la déclaration dans le fichier ColumnGuideCommands.cs, mais vous allez remplacer le contenu de ce fichier Par conséquent, les GUID correspond à.  
  
 Autres GUID dans le fichier .vsct identifient les menus préexistants à laquelle les commandes de guide de colonne sont ajoutés, afin qu’ils ne changent jamais.  
  
 **Sections du fichier**.  Le .vsct a trois sections externes : commandes, des emplacements et des symboles.  La section commandes définit les groupes de commandes, des menus, des boutons ou des éléments de menu et des bitmaps pour les icônes.  La section placements déclare où adresser des groupes dans les menus ou des emplacements supplémentaires sur les menus préexistants.  La section symboles déclare des identificateurs utilisés ailleurs dans le fichier .vsct, ce qui rend le code .vsct plus lisible qu’ayant le GUID et les nombres hexadécimaux partout.  
  
 **Section des commandes, de groupes de définitions**.  La section commandes définit tout d’abord les groupes de commandes.  Groupes de commandes sont des commandes de menus avec les lignes grises légères séparant les groupes.  Un groupe peut se remplir également un sous-menu entière, comme dans cet exemple, et vous ne voyez pas le gris séparant les lignes dans ce cas.  Les fichiers .vsct déclare deux groupes, la `GuidesMenuItemsGroup` qui est apparentée à la `IDM_VS_MENU_EDIT` (principal **modifier** menu) et le `GuidesContextMenuGroup` qui est apparentée à la `IDM_VS_CTXT_CODEWIN` (menu contextuel de l’éditeur de code).  
  
 La seconde déclaration de groupe a un `0x0600` priorité :  
  
```xml  
<Group guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"   
             priority="0x0600">  
```  
  
 L’idée est de placer la colonne guides de sous-menu à la fin d’un menu contextuel dans lequel nous ajouter le groupe de menus sub.  Toutefois, vous devez supposer pas de vous connaissez mieux et forcez le sous-menu à toujours être le dernier à l’aide d’une priorité de `0xFFFF`.  Vous devez utiliser ce nombre pour voir où votre menu sub se trouve sur l’endroit où vous le placez les menus contextuels.  Dans ce cas `0x0600` est suffisamment élevé pour le placer à la fin des menus pour autant que nous pouvons voir, mais laisse de place pour quelqu'un d’autre à leur extension soit inférieur à l’extension de repères de colonne si ce n’est souhaitable de conception.  
  
 **Section, définition du menu de commandes**.  Ensuite la commande définit le sous-menu `GuidesSubMenu`apparenté à la `GuidesContextMenuGroup`.  Le `GuidesContextMenuGroup` est le groupe que nous ajoutons à tous les menus le contexte pertinent.  Dans la section emplacements, le code place le groupe avec les commandes de guide de quatre colonnes de ce menu sub.  
  
 **Section des commandes, boutons définitions**.  La section commandes définit ensuite les éléments de menu ou boutons de la colonne quatre guides de commandes.  `CommandWellOnly`, décrits ci-dessus, signifie que les commandes sont invisibles lorsqu’elle est placée dans un menu principal.  Deux de l’élément de menu bouton déclarations (guide d’ajouter et supprimer des guide) ont également un `AllowParams` indicateur :  
  
```xml  
<CommandFlag>AllowParams</CommandFlag>  
```  
  
 Cet indicateur permet ainsi d’avoir des emplacements de menu principal, la commande pour recevoir des arguments lorsque Visual Studio appelle le Gestionnaire de commandes.  Si l’utilisateur appelle la commande à partir de la fenêtre de commande, l’argument passé au Gestionnaire de commandes de l’événement arguments.  
  
 **Sections de commande, les définitions de bitmaps**.  Enfin, la section commandes déclare les bitmaps ou des icônes utilisées pour les commandes.  Il s’agit d’une déclaration simple qui identifie la ressource de projet et répertorie les index de base un d’icônes utilisées.  La section de symboles du fichier .vsct déclare les valeurs des identificateurs utilisés en tant qu’index.  Cette procédure pas à pas utilise la bande d’image bitmap fournie avec le modèle d’élément de commande personnalisée ajouté au projet.  
  
 **Section des placements**.  Après les commandes section est la section de la sélection élective.  La première est où le code ajoute du premier groupe ci-dessus qui conserve le guide de la quatre colonne commandes au menu sub où les commandes s’affichent :  
  
```xml  
<CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"   
                  priority="0x0100">  
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" />  
</CommandPlacement>  
```  
  
 Tous les autres emplacements ajouter la `GuidesContextMenuGroup` (qui contient le `GuidesSubMenu`) pour les autres menus contextuels de l’éditeur.  Lorsque le code est déclarée la `GuidesContextMenuGroup`, il a été apparenté au menu contextuel de l’éditeur de code.  C’est pourquoi vous ne voyez pas un emplacement pour le menu contextuel de l’éditeur de code.  
  
 **Section des symboles**.  Comme indiqué ci-dessus, la section symboles déclare des identificateurs utilisés ailleurs dans le fichier .vsct, ce qui rend le code .vsct plus lisible qu’ayant le GUID et les nombres hexadécimaux partout.  Les points importants de cette section sont que le GUID du package doit correspondre à la déclaration de que GUID doit correspondre à la déclaration de la classe d’implémentation de commande dans la classe de package et le jeu de commandes.  
  
## <a name="implementing-the-commands"></a>Implémentation des commandes  
 Le fichier ColumnGuideCommands.cs implémente les commandes et raccorde les gestionnaires.  Lorsque Visual Studio charge le package et l’initialise, le package est à son tour appelle `Initialize` sur la classe d’implémentation de commandes.  L’initialisation de commandes instancie simplement la classe, et le constructeur raccorde les gestionnaires de commandes.  
  
 Remplacez le contenu du fichier ColumnGuideCommands.cs par le code suivant (voir ci-après) :  
  
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
  
 **Résoudre les références**.  Il manque une référence à ce stade.  Appuyez sur le bouton droit du pointeur sur le nœud Références dans l’Explorateur de solutions.  Choisissez le **ajouter...**  commande.  Le **ajouter une référence** boîte de dialogue comprend une zone de recherche dans le coin supérieur droit.  Entrez « éditeur » (sans les guillemets doubles).  Choisissez le **Microsoft.VisualStudio.Editor** élément (vous devez cocher la case à gauche de l’élément, sélectionnez simplement l’élément) et choisissez **OK** pour ajouter la référence.  
  
 **L’initialisation**.  Lors de l’initialisation de la classe de package, il appelle `Initialize` sur la classe d’implémentation de commandes.  Le `ColumnGuideCommands` initialisation instancie la classe et enregistre l’instance de classe et de la référence de package dans les membres de classe.  
  
 Examinons un de l’onduleur de raccordement de gestionnaire de commandes à partir du constructeur de classe :  
  
```csharp  
_addGuidelineCommand =   
    new OleMenuCommand(AddColumnGuideExecuted, null,  
                       AddColumnGuideBeforeQueryStatus,  
                       new CommandID(ColumnGuideCommands.CommandSet,  
                                     cmdidAddColumnGuide));  
  
```  
  
 Vous créez un `OleMenuCommand`.  Visual Studio utilise le système de commande de Microsoft Office.  Les arguments de clés lors de l’instanciation d’un OleMenuCommand est la fonction qui implémente la commande (`AddColumnGuideExecuted`), la fonction à appeler lorsque Visual Studio affiche un menu avec la commande (`AddColumnGuideBeforeQueryStatus`) et l’ID de commande.  Visual studio appelle la fonction d’état de requête avant l’affichage d’une commande dans un menu afin que la commande peut rendre invisible ou grisé pour un affichage du menu (par exemple, la désactivation **copie** si aucune sélection), modifier son icône, ou encore modifier son nom (par exemple, d’ajouter un élément à supprimer un élément) et ainsi de suite.  L’ID de commande doit correspondre à un ID de commande déclaré dans le fichier .vsct.  Définir des chaînes pour la commande et les repères de colonne Ajouter la commande doit correspondre entre le fichier .vsct et le ColumnGuideCommands.cs.  
  
 La ligne suivante fournit une assistance pour des utilisateurs appeler la commande via la fenêtre de commande (voir ci-après) :  
  
```csharp  
_addGuidelineCommand.ParametersDescription = "<column>";  
```  
  
 **Interroger l’état**.  Les fonctions d’état de requête `AddColumnGuideBeforeQueryStatus` et `RemoveColumnGuideBeforeQueryStatus` vérifier certains paramètres (tels que le nombre maximal de guides ou colonne max) ou s’il existe un repère de colonne à supprimer.  Elles permettent les commandes si les conditions sont remplies.  Fonctions d’état de requête doivent être très efficaces car elles s’exécutent chaque fois que Visual Studio affiche un menu pour chaque commande dans le menu.  
  
 **Fonction de AddColumnGuideExecuted**.  La partie intéressante d’ajout d’un repère est de déterminer l’emplacement d’affichage et le signe insertion éditeur actuel.  Cette fonction appelle d’abord `GetApplicableColumn` qui vérifie s’il existe un argument fourni par l’utilisateur dans les arguments d’événement du Gestionnaire de commandes et s’il en existe aucun, la fonction vérifie le mode de l’éditeur :  
  
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
  
 `GetCurrentEditorColumn`a d’aller un peu plus pour obtenir un <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> affichage du code.  Si vous tracez `GetActiveTextView`, `GetActiveView`, et `GetTextViewFromVsTextView`, vous pouvez voir comment le faire.  Voici le code abstrait, en commençant par la sélection actuelle, mise en route du frame de la sélection, puis mise en route de DocView du frame comme un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>, puis en une <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> à partir de la IVsTextView, puis l’obtention d’un hôte de la vue, et enfin le IWpfTextView :  
  
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
  
 Une fois que vous avez une IWpfTextView, vous pouvez obtenir la colonne où se trouve le point d’insertion :  
  
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
  
 Avec la colonne actuelle en cours lorsque l’utilisateur a cliqué, le code appelle simplement sur le Gestionnaire de paramètres pour ajouter ou supprimer la colonne.  Le Gestionnaire de paramètres déclenche l’événement pour lequel toutes les `ColumnGuideAdornment` écoutent des objets.  Lorsque l’événement se déclenche, ces objets de mettre à jour leur point de vue de texte associé avec les nouveaux paramètres de guide de colonne.  
  
## <a name="invoking-command-from-the-command-window"></a>Appel de commande à partir de la fenêtre de commande  
 L’exemple de repères de colonne permet aux utilisateurs d’appeler deux commandes à partir de la fenêtre de commande en tant que formulaire d’extensibilité.  Si vous utilisez la **View &#124; Autres fenêtres &#124; Fenêtre de commande** de commandes, vous pouvez voir la fenêtre de commande.  Vous pouvez interagir avec la fenêtre de commande en entrant « modifier », et avec la saisie semi-automatique de nom de commande et en fournissant l’argument 120, vous disposez des éléments suivants :  
  
```  
> Edit.AddColumnGuide 120  
>  
```  
  
 Les éléments de l’exemple qui sont dans les déclarations de fichier .vsct, le `ColumnGuideCommands` constructeur de classe lorsqu’il intercepte les gestionnaires de commandes et les implémentations de gestionnaire de commandes qui vérifient les arguments d’événement.  
  
 Vous avez vu «`<CommandFlag>CommandWellOnly</CommandFlag>`» dans le fichier .vsct, ainsi que les emplacements dans le menu principal de modifier bien que nous ne pas afficher les commandes dans le **modifier** menu de l’interface utilisateur.  Leur présence sur le menu principal de modifier leur donne des noms tels que **Edit.AddColumnGuide**.  Les commandes de groupe déclaration qui contient que les quatre commandes placé directement le groupe dans le menu Edition :  
  
```xml  
<Group guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"  
             priority="0xB801">  
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_EDIT" />  
      </Group>  
  
```  
  
 La section boutons déclarée les commandes `CommandWellOnly` les conserver dans le menu principal invisible et déclaré avec `AllowParams`:  
  
```xml  
<Button guid="guidColumnGuidesCommandSet" id="cmdidAddColumnGuide"   
        priority="0x0100" type="Button">  
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />  
  <Icon guid="guidImages" id="bmpPicAddGuide" />  
  <CommandFlag>CommandWellOnly</CommandFlag>  
  <CommandFlag>AllowParams</CommandFlag>  
  
```  
  
 Vous avez vu le Gestionnaire de commandes de raccorder le code dans le `ColumnGuideCommands` constructeur de classe fournissiez une description du paramètre autorisé :  
  
```csharp  
_addGuidelineCommand.ParametersDescription = "<column>";  
  
```  
  
 Vous avez vu le `GetApplicableColumn` vérifications de la fonction `OleMenuCmdEventArgs` pour une valeur avant la vérification de la vue de l’éditeur pour une colonne en cours :  
  
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
  
## <a name="trying-your-extension"></a>La tentative de votre Extension  
 Vous pouvez désormais appuyer sur **F5** pour exécuter votre extension de repères de colonne.  Ouvrir un fichier texte et utiliser le menu contextuel de l’éditeur pour ajouter des lignes de repère, de les supprimer et de modifier leur couleur.  Vous devez cliquer dans le texte (pas d’espace blanc passée à la fin de la ligne) pour ajouter une colonne guide ou l’éditeur ajoute à la dernière colonne de la ligne.  Si vous utilisez la fenêtre de commande et appelez les commandes avec un argument, vous pouvez ajouter des repères de colonne n’importe où.  
  
 Si vous souhaitez essayer placements de commandes différentes, modifier les noms, modifier les icônes et ainsi de suite, et que vous rencontrez des problèmes avec Visual Studio affiche le dernier code de menus, vous pouvez réinitialiser la ruche expérimentale, dans lequel vous effectuez un débogage.  Afficher le **Menu Démarrer de Windows** et tapez « réinitialiser ».  Rechercher et appeler la commande **réinitialiser l’Instance expérimentale Visual Studio suivant**.  Cette opération nettoie la ruche du Registre expérimentale de tous les composants d’extension.  Il n’existe pas nettoyer les paramètres à partir des composants, par conséquent, n’importe quel repère que vous aviez lorsque vous arrêtez la ruche expérimentale de Visual Studio sera toujours présente lorsque votre code lit le stockage de paramètres au lancement suivant.  
  
## <a name="finished-code-project"></a>Projet de Code terminé  
 Il y aura bientôt d’un projet github d’exemples d’extensibilité de Visual Studio, et le projet achevé sera présente.  Nous mettrons à jour cette rubrique pour pointer il lorsque cela se produit.  L’exemple terminé de projet peut avoir des GUID différents et ont une bande de bitmaps différentes pour les icônes de commande.  
  
 Vous pouvez essayer une version de la fonctionnalité de repères de colonne avec cette galerie Visual Studio[extension](https://visualstudiogallery.msdn.microsoft.com/da227a0b-0e31-4a11-8f6b-3a149cf2e459?SRC=Home).  
  
## <a name="see-also"></a>Voir aussi  
 [Dans l’éditeur](../extensibility/inside-the-editor.md)   
 [Extension de l’éditeur et Services de langage](../extensibility/extending-the-editor-and-language-services.md)   
 [Service de langage et les Points d’Extension de l’éditeur](../extensibility/language-service-and-editor-extension-points.md)   
 [Extension des Menus et commandes](../extensibility/extending-menus-and-commands.md)   
 [Ajout d’un sous-menu à un Menu](../extensibility/adding-a-submenu-to-a-menu.md)   
 [Création d’une extension avec un modèle d’élément d’éditeur](../extensibility/creating-an-extension-with-an-editor-item-template.md)
