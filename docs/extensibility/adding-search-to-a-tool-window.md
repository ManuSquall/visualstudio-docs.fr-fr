---
title: "Ajout d’une fenêtre outil recherche | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tool windows, adding search
ms.assetid: f78c4892-8060-49c4-8ecd-4360f1b4d133
caps.latest.revision: 38
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
translationtype: Machine Translation
ms.sourcegitcommit: bca8c87d4f7d89d491fab13e1a511febce81d3d8
ms.openlocfilehash: 845bbc5c34280f7ceafcaa3d763065f6d73388fe
ms.lasthandoff: 02/22/2017

---
# <a name="adding-search-to-a-tool-window"></a>Ajout de la recherche dans une fenêtre outil
Lorsque vous créez ou mettez à jour une fenêtre outil dans votre extension, vous pouvez ajouter la fonctionnalité de recherche apparaît ailleurs dans Visual Studio. Cette fonctionnalité inclut les fonctionnalités suivantes :  
  
-   Une zone de recherche qui se trouve toujours dans une zone de la barre d’outils personnalisée.  
  
-   Un indicateur de progression est placée dans la zone de recherche.  
  
-   La possibilité d’afficher les résultats dès que vous entrez chaque caractère (recherche instantanée) ou uniquement une fois que vous appuyez sur la touche entrée (recherche à la demande).  
  
-   Liste des termes du contrat pour lequel vous avez récemment recherchée.  
  
-   Permet de filtrer les recherches par des champs ou des aspects des cibles de recherche.  
  
 En suivant cette procédure pas à pas, vous allez apprendre à effectuer les tâches suivantes :  
  
1.  Créez un projet VSPackage.  
  
2.  Créer une fenêtre Outil contenant un contrôle utilisateur avec un contrôle TextBox en lecture seule.  
  
3.  Ajoutez une zone de recherche dans la fenêtre outil.  
  
4.  Ajoutez l’implémentation de la recherche.  
  
5.  Activer la recherche instantanée et l’affichage d’une barre de progression.  
  
6.  Ajouter un **respecter la casse** option.  
  
7.  Ajouter un **recherche uniquement les lignes paires** filtre.  
  
## <a name="to-create-a-vsix-project"></a>Pour créer un projet VSIX  
  
1.  Créez un projet VSIX nommé `TestToolWindowSearch` avec une fenêtre Outil nommée **TestSearch**. Si vous avez besoin d’aide cette opération, consultez la page [création d’une Extension avec une fenêtre outil](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="to-create-a-tool-window"></a>Pour créer une fenêtre outil  
  
1.  Dans la `TestToolWindowSearch` de projet, ouvrez le fichier TestSearchControl.xaml.  
  
2.  Remplacez la `<StackPanel>` bloc avec le bloc suivant, qui ajoute en lecture seule <xref:System.Windows.Controls.TextBox>à la <xref:System.Windows.Controls.UserControl>dans la fenêtre outil.</xref:System.Windows.Controls.UserControl> </xref:System.Windows.Controls.TextBox>  
  
    ```xaml  
    <StackPanel Orientation="Vertical">  
        <TextBox Name="resultsTextBox" Height="800.0"  
            Width="800.0"  
            IsReadOnly="True">  
        </TextBox>  
    </StackPanel>  
    ```  
  
3.  Dans le fichier TestSearchControl.xaml.cs, ajoutez l’instruction using :  
  
    ```c#  
    using System.Text;  
    ```  
  
4.  Supprimer le `button1_Click()` (méthode).  
  
     Dans le **TestSearchControl** de classe, ajoutez le code suivant.  
  
     Ce code ajoute un public <xref:System.Windows.Controls.TextBox>propriété nommée **SearchResultsTextBox** et une propriété de chaîne publique nommée **SearchContent**.</xref:System.Windows.Controls.TextBox> Dans le constructeur, SearchResultsTextBox est définie sur la zone de texte et SearchContent est initialisé à un ensemble de saut de ligne délimitée par des chaînes. Le contenu de la zone de texte est également initialisé à l’ensemble de chaînes.  
  
    ```c#  
    public partial class TestSearchControl : UserControl  
    {  
        public TextBox SearchResultsTextBox { get; set; }  
        public string SearchContent { get; set; }  
  
        public TestSearchControl()  
        {  
            InitializeComponent();  
  
            this.SearchResultsTextBox = resultsTextBox;  
            this.SearchContent = BuildContent();  
  
            this.SearchResultsTextBox.Text = this.SearchContent;  
        }  
  
        private string BuildContent()  
        {  
            StringBuilder sb = new StringBuilder();  
            sb.AppendLine("1 go");  
            sb.AppendLine("2 good");  
            sb.AppendLine("3 Go");  
            sb.AppendLine("4 Good");  
            sb.AppendLine("5 goodbye");  
            sb.AppendLine("6 Goodbye");  
  
            return sb.ToString();  
        }  
    }  
    ```  
  
     [!code-cs[N °&1; de ToolWindowSearch](../extensibility/codesnippet/CSharp/adding-search-to-a-tool-window_1.cs) ] 
     [!code-vb [ToolWindowSearch n °&1;](../extensibility/codesnippet/VisualBasic/adding-search-to-a-tool-window_1.vb)]  
  
5.  Générez le projet et commencez le débogage. L’instance expérimentale de Visual Studio s’affiche.  
  
6.  Dans la barre de menus, choisissez **affichage**, **autres fenêtres**, **TestSearch**.  
  
     La fenêtre d’outils s’affiche, mais le contrôle de recherche n’apparaît pas encore.  
  
## <a name="to-add-a-search-box-to-the-tool-window"></a>Pour ajouter une zone de recherche dans la fenêtre outil  
  
1.  Dans le fichier TestSearch.cs, ajoutez le code suivant à la `TestSearch` classe. Le code substitue la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A>propriété afin que l’accesseur get retourne `true`.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A>  
  
     Pour activer la recherche, vous devez substituer les <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A>propriété.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> La <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>classe implémente <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch>et fournit une implémentation par défaut qui ne permet pas recherche.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch> </xref:Microsoft.VisualStudio.Shell.ToolWindowPane>  
  
    ```c#  
    public override bool SearchEnabled  
    {  
        get { return true; }  
    }  
    ```  
  
2.  Générez le projet et commencez le débogage. L’instance expérimentale s’affiche.  
  
3.  Dans l’instance expérimentale de Visual Studio, ouvrez **TestSearch**.  
  
     En haut de la fenêtre outil, un contrôle de recherche s’affiche avec un **recherche** filigrane et une icône de verre agrandissement. Toutefois, recherche ne fonctionne pas encore, car le processus de recherche n’a pas été implémenté.  
  
## <a name="to-add-the-search-implementation"></a>Pour ajouter l’implémentation de la recherche  
 Lorsque vous activez la recherche sur un <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>, comme dans la procédure précédente, la fenêtre de l’outil crée un hôte de recherche.</xref:Microsoft.VisualStudio.Shell.ToolWindowPane> Cet hôte configure et gère les processus de recherche, qui se produisent toujours sur un thread d’arrière-plan. Étant donné que la <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>classe gère la création de l’hôte de la recherche et la configuration de la recherche, vous devez uniquement créer une tâche de recherche et fournit la méthode de recherche.</xref:Microsoft.VisualStudio.Shell.ToolWindowPane> Le processus de recherche se produit sur un thread d’arrière-plan, et les appels pour le contrôle de fenêtre outil se produisent sur le thread d’interface utilisateur. Par conséquent, vous devez utiliser le <xref:Microsoft.VisualStudio.Shell.ThreadHelper.Invoke%2A>méthode pour gérer les appels que vous effectuez en intégrant le contrôle.</xref:Microsoft.VisualStudio.Shell.ThreadHelper.Invoke%2A>  
  
1.  Dans le fichier TestSearch.cs, ajoutez le code suivant `using` instructions :  
  
    ```c#  
    using System;  
    using System.Collections.Generic;  
    using System.Runtime.InteropServices;  
    using System.Text;  
    using System.Windows.Controls;  
    using Microsoft.Internal.VisualStudio.PlatformUI;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.PlatformUI;  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
2.  Dans la `TestSearch` de classe, ajoutez le code suivant, qui effectue les actions suivantes :  
  
    -   Remplace la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch>méthode pour créer une tâche de recherche.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch>  
  
    -   Remplace la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A>méthode pour restaurer l’état de la zone de texte.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> Cette méthode est appelée lorsqu’un utilisateur annule une tâche de recherche et lorsqu’un utilisateur définit ou unsets options ou filtres. Les deux <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A>et <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A>sont appelées sur le thread d’interface utilisateur.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> Par conséquent, vous n’avez pas besoin accéder à la zone de texte au moyen de la <xref:Microsoft.VisualStudio.Shell.ThreadHelper.Invoke%2A>méthode.</xref:Microsoft.VisualStudio.Shell.ThreadHelper.Invoke%2A>  
  
    -   Crée une classe nommée `TestSearchTask` qui hérite <xref:Microsoft.VisualStudio.Shell.VsSearchTask>, qui fournit une implémentation par défaut de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSearchTask>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSearchTask> </xref:Microsoft.VisualStudio.Shell.VsSearchTask>  
  
         Dans `TestSearchTask`, le constructeur définit un champ privé qui fait référence à la fenêtre outil. Pour fournir la méthode de recherche, vous substituez le <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A>et <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStopSearch%2A>méthodes.</xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStopSearch%2A> </xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> La <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A>consiste où vous implémentez le processus de recherche.</xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> Ce processus inclut la recherche, afficher les résultats de recherche dans la zone de texte et l’appel de l’implémentation de classe de base de cette méthode pour signaler que la recherche est terminée.  
  
    ```c#  
    public override IVsSearchTask CreateSearch(uint dwCookie, IVsSearchQuery pSearchQuery, IVsSearchCallback pSearchCallback)  
    {  
        if (pSearchQuery == null || pSearchCallback == null)  
            return null;  
         return new TestSearchTask(dwCookie, pSearchQuery, pSearchCallback, this);  
    }  
  
    public override void ClearSearch()  
    {  
        TestSearchControl control = (TestSearchControl)this.Content;  
        control.SearchResultsTextBox.Text = control.SearchContent;  
    }  
  
    internal class TestSearchTask : VsSearchTask  
    {  
        private TestSearch m_toolWindow;  
  
        public TestSearchTask(uint dwCookie, IVsSearchQuery pSearchQuery, IVsSearchCallback pSearchCallback, TestSearch toolwindow)  
            : base(dwCookie, pSearchQuery, pSearchCallback)  
        {  
            m_toolWindow = toolwindow;  
        }  
  
        protected override void OnStartSearch()  
        {  
            // Use the original content of the text box as the target of the search.   
            var separator = new string[] { Environment.NewLine };  
            TestSearchControl control = (TestSearchControl)m_toolWindow.Content;  
            string[] contentArr = control.SearchContent.Split(separator, StringSplitOptions.None);  
  
            // Get the search option.   
            bool matchCase = false;  
            // matchCase = m_toolWindow.MatchCaseOption.Value;   
  
                // Set variables that are used in the finally block.  
                StringBuilder sb = new StringBuilder("");  
                uint resultCount = 0;  
                this.ErrorCode = VSConstants.S_OK;  
  
                try  
                {  
                    string searchString = this.SearchQuery.SearchString;  
  
                    // Determine the results.   
                    uint progress = 0;  
                    foreach (string line in contentArr)  
                    {  
                        if (matchCase == true)  
                        {  
                            if (line.Contains(searchString))  
                            {  
                                sb.AppendLine(line);  
                                resultCount++;  
                            }  
                        }  
                        else  
                            {  
                                if (line.ToLower().Contains(searchString.ToLower()))  
                                {  
                                    sb.AppendLine(line);  
                                    resultCount++;  
                                }  
                            }  
  
                            // SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));   
  
                            // Uncomment the following line to demonstrate the progress bar.   
                            // System.Threading.Thread.Sleep(100);  
                        }  
                    }  
                    catch (Exception e)  
                    {  
                        this.ErrorCode = VSConstants.E_FAIL;  
                    }  
                    finally  
                    {  
                        ThreadHelper.Generic.Invoke(() =>  
                        { ((TextBox)((TestSearchControl)m_toolWindow.Content).SearchResultsTextBox).Text = sb.ToString(); });  
  
                        this.SearchResults = resultCount;  
                    }  
  
            // Call the implementation of this method in the base class.   
            // This sets the task status to complete and reports task completion.   
            base.OnStartSearch();  
        }  
  
        protected override void OnStopSearch()  
        {  
            this.SearchResults = 0;  
        }  
    }  
    ```  
  
3.  Testez votre implémentation de recherche en effectuant les opérations suivantes :  
  
    1.  Régénérez le projet et démarrer le débogage.  
  
    2.  Dans l’instance expérimentale de Visual Studio, ouvrez de nouveau la fenêtre outil, entrez du texte de recherche dans la fenêtre de recherche et appuyez sur ENTRÉE.  
  
         Les résultats corrects doivent apparaître.  
  
## <a name="to-customize-the-search-behavior"></a>Pour personnaliser le comportement de recherche  
 En modifiant les paramètres de recherche, vous pouvez apporter différentes des modifications dans la façon dont le contrôle de recherche apparaît et comment la recherche est effectuée. Par exemple, vous pouvez modifier le filigrane (le texte par défaut qui s’affiche dans la zone de recherche), la valeur minimale et la largeur maximale du contrôle de recherche et s’il faut afficher une barre de progression. Vous pouvez également modifier le point sur les résultats Démarrer (à la demande ou sur la recherche instantanée) et s’il faut afficher une liste de termes que vous avez récemment recherché. Vous trouverez la liste complète des paramètres dans la <xref:Microsoft.VisualStudio.PlatformUI.SearchSettingsDataSource>classe.</xref:Microsoft.VisualStudio.PlatformUI.SearchSettingsDataSource>  
  
1.  Dans le fichier TestSearch.cs, ajoutez le code suivant à la `TestSearch` classe. Ce code permet la recherche instantanée au lieu de la recherche à la demande (ce qui signifie que l’utilisateur n’ait à cliquer sur entrée). Le code substitue la `ProvideSearchSettings` méthode dans la `TestSearch` classe, qui est nécessaire pour modifier les paramètres par défaut.  
  
    ```c#  
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)  
    {  
        Utilities.SetValue(pSearchSettings,   
            SearchSettingsDataSource.SearchStartTypeProperty.Name,   
            (uint)VSSEARCHSTARTTYPE.SST_INSTANT);}  
    ```  
  
2.  Tester le nouveau paramètre, régénérer la solution, puis redémarrer le débogueur.  
  
     Affichage des résultats chaque fois que vous entrez un caractère dans la zone de recherche.  
  
3.  Dans le `ProvideSearchSettings` (méthode), ajoutez la ligne suivante, qui permet d’afficher une barre de progression.  
  
    ```c#  
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)  
    {  
        Utilities.SetValue(pSearchSettings,   
            SearchSettingsDataSource.SearchStartTypeProperty.Name,   
             (uint)VSSEARCHSTARTTYPE.SST_INSTANT);  
        Utilities.SetValue(pSearchSettings,   
            SearchSettingsDataSource.SearchProgressTypeProperty.Name,   
             (uint)VSSEARCHPROGRESSTYPE.SPT_DETERMINATE);  
    }  
    ```  
  
     Pour la barre de progression à afficher la progression doit être signalée. Pour signaler la progression, supprimez le code suivant dans le `OnStartSearch` procédé de la `TestSearchTask` classe :  
  
    ```c#  
    SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));  
    ```  
  
4.  Pour ralentir la progression du traitement suffisamment barre s’affiche, supprimez les commentaires de la ligne suivante dans le `OnStartSearch` procédé de la `TestSearchTask` classe :  
  
    ```c#  
    System.Threading.Thread.Sleep(100);  
    ```  
  
5.  Les nouveaux paramètres de test par la régénération de la solution et commencer à debugb.  
  
     La barre de progression s’affiche dans la fenêtre de recherche (comme une ligne bleue sous la zone de texte Rechercher) chaque fois que vous effectuez une recherche.  
  
## <a name="to-enable-users-to-refine-their-searches"></a>Pour permettre aux utilisateurs d’affiner leurs recherches  
 Vous pouvez permettre aux utilisateurs d’affiner leurs recherches au moyen des options telles que **respecter la casse** ou **mot entier**. Options peuvent être boolean, qui apparaissent comme des cases à cocher, ou des commandes qui s’affichent sous forme de boutons. Pour cette procédure pas à pas, vous allez créer une option de type boolean.  
  
1.  Dans le fichier TestSearch.cs, ajoutez le code suivant à la `TestSearch` classe. Le code substitue la `SearchOptionsEnum` (méthode), ce qui permet l’implémentation détecter si une option donnée est activée ou désactivée. Le code dans `SearchOptionsEnum` ajoute une option permettant de respecter la casse pour un <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumWindowSearchOptions>énumérateur.</xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumWindowSearchOptions> L’option pour respecter la casse est également mises à disposition en tant que le `MatchCaseOption` propriété.  
  
    ```c#  
    private IVsEnumWindowSearchOptions m_optionsEnum;  
    public override IVsEnumWindowSearchOptions SearchOptionsEnum  
    {  
        get  
        {  
            if (m_optionsEnum == null)  
            {  
                List<IVsWindowSearchOption> list = new List<IVsWindowSearchOption>();  
  
                list.Add(this.MatchCaseOption);  
  
                m_optionsEnum = new WindowSearchOptionEnumerator(list) as IVsEnumWindowSearchOptions;  
            }  
            return m_optionsEnum;  
        }  
    }  
  
    private WindowSearchBooleanOption m_matchCaseOption;  
    public WindowSearchBooleanOption MatchCaseOption  
    {  
        get  
        {  
            if (m_matchCaseOption == null)  
            {  
                m_matchCaseOption = new WindowSearchBooleanOption("Match case", "Match case", false);  
            }  
            return m_matchCaseOption;  
        }  
    }  
    ```  
  
2.  Dans le `TestSearchTask` (classe), supprimez les commentaires ligne matchCase dans le `OnStartSearch` méthode :  
  
    ```c#  
    private IVsEnumWindowSearchOptions m_optionsEnum;  
    public override IVsEnumWindowSearchOptions SearchOptionsEnum  
    {  
        get  
        {  
            if (m_optionsEnum == null)  
            {  
                List<IVsWindowSearchOption> list = new List<IVsWindowSearchOption>();  
  
                list.Add(this.MatchCaseOption);  
  
                m_optionsEnum = new WindowSearchOptionEnumerator(list) as IVsEnumWindowSearchOptions;  
            }  
            return m_optionsEnum;  
        }  
    }  
  
    private WindowSearchBooleanOption m_matchCaseOption;  
    public WindowSearchBooleanOption MatchCaseOption  
    {  
        get  
         {  
            if (m_matchCaseOption == null)  
            {  
                m_matchCaseOption = new WindowSearchBooleanOption("Match case", "Match case", false);  
            }  
            return m_matchCaseOption;  
        }  
    }  
    ```  
  
3.  L’option de test :  
  
    1.  Générez le projet et commencez le débogage. L’instance expérimentale s’affiche.  
  
    2.  Dans la fenêtre d’outils, cliquez sur la flèche située à droite de la zone de texte.  
  
         Le **respecter la casse** case à cocher s’affiche.  
  
    3.  Sélectionnez le **respecter la casse** case à cocher et d’effectuer des recherches.  
  
## <a name="to-add-a-search-filter"></a>Pour ajouter un filtre de recherche  
 Vous pouvez ajouter des filtres de recherche qui permettent aux utilisateurs d’affiner l’ensemble des cibles de recherche. Par exemple, vous pouvez filtrer les fichiers dans l’Explorateur de fichiers par les dates à laquelle ils ont été récemment modifiés et leurs extensions de nom de fichier. Dans cette procédure pas à pas, vous allez ajouter un filtre de lignes paires uniquement. Lorsque l’utilisateur choisit ce filtre, la recherche ajoute les chaînes que vous spécifiez à la requête de recherche. Vous pouvez identifier ces chaînes à l’intérieur de votre méthode de recherche et filtrer les cibles de recherche en conséquence.  
  
1.  Dans le fichier TestSearch.cs, ajoutez le code suivant à la `TestSearch` classe. Le code implémente `SearchFiltersEnum` en ajoutant un <xref:Microsoft.VisualStudio.PlatformUI.WindowSearchSimpleFilter>qui spécifie pour filtrer les résultats de recherche afin que seules les lignes même apparaissent.</xref:Microsoft.VisualStudio.PlatformUI.WindowSearchSimpleFilter>  
  
    ```c#  
    public override IVsEnumWindowSearchFilters SearchFiltersEnum  
    {  
        get  
        {  
            List<IVsWindowSearchFilter> list = new List<IVsWindowSearchFilter>();  
            list.Add(new WindowSearchSimpleFilter("Search even lines only", "Search even lines only", "lines", "even"));  
            return new WindowSearchFilterEnumerator(list) as IVsEnumWindowSearchFilters;  
        }  
    }  
  
    ```  
  
     Maintenant le contrôle de recherche affiche le filtre de recherche `Search even lines only`. Lorsque l’utilisateur choisit le filtre, la chaîne `lines:"even"` s’affiche dans la zone de recherche. Autres critères de recherche peuvent apparaître en même temps que le filtre. Chaînes de recherche peuvent apparaître avant le filtre, après le filtre, ou les deux.  
  
2.  Dans le fichier TestSearch.cs, ajoutez les méthodes suivantes pour le `TestSearchTask` (classe), qui se trouve dans le `TestSearch` (classe). Ces méthodes prennent en charge la `OnStartSearch` (méthode), que vous modifierez à l’étape suivante.  
  
    ```c#  
    private string RemoveFromString(string origString, string stringToRemove)  
    {  
        int index = origString.IndexOf(stringToRemove);  
        if (index == -1)  
            return origString;  
        else   
             return (origString.Substring(0, index) + origString.Substring(index + stringToRemove.Length)).Trim();  
    }  
  
    private string[] GetEvenItems(string[] contentArr)  
    {  
        int length = contentArr.Length / 2;  
        string[] evenContentArr = new string[length];  
  
        int indexB = 0;  
        for (int index = 1; index < contentArr.Length; index += 2)  
        {  
            evenContentArr[indexB] = contentArr[index];  
            indexB++;  
        }  
  
        return evenContentArr;  
    }  
    ```  
  
3.  Dans le `TestSearchTask` de classe, de mettre à jour le `OnStartSearch` méthode par le code suivant. Cette modification met à jour le code pour prendre en charge le filtre.  
  
    ```c#  
    protected override void OnStartSearch()  
    {  
        // Use the original content of the text box as the target of the search.   
        var separator = new string[] { Environment.NewLine };  
        string[] contentArr = ((TestSearchControl)m_toolWindow.Content).SearchContent.Split(separator, StringSplitOptions.None);  
  
        // Get the search option.   
        bool matchCase = false;  
        matchCase = m_toolWindow.MatchCaseOption.Value;  
  
        // Set variables that are used in the finally block.  
        StringBuilder sb = new StringBuilder("");  
        uint resultCount = 0;  
        this.ErrorCode = VSConstants.S_OK;  
  
        try  
        {  
            string searchString = this.SearchQuery.SearchString;  
  
            // If the search string contains the filter string, filter the content array.   
            string filterString = "lines:\"even\"";  
  
            if (this.SearchQuery.SearchString.Contains(filterString))  
            {  
                // Retain only the even items in the array.  
                contentArr = GetEvenItems(contentArr);  
  
                // Remove 'lines:"even"' from the search string.  
                searchString = RemoveFromString(searchString, filterString);  
            }  
  
            // Determine the results.   
            uint progress = 0;  
            foreach (string line in contentArr)  
            {  
                if (matchCase == true)  
                {  
                    if (line.Contains(searchString))  
                    {  
                        sb.AppendLine(line);  
                        resultCount++;  
                    }  
                }  
                else  
                {  
                    if (line.ToLower().Contains(searchString.ToLower()))  
                    {  
                        sb.AppendLine(line);  
                        resultCount++;  
                    }  
                }  
  
                SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));  
  
                // Uncomment the following line to demonstrate the progress bar.   
                // System.Threading.Thread.Sleep(100);  
            }  
        }  
        catch (Exception e)  
        {  
            this.ErrorCode = VSConstants.E_FAIL;  
        }  
        finally  
        {  
            ThreadHelper.Generic.Invoke(() =>  
            { ((TextBox)((TestSearchControl)m_toolWindow.Content).SearchResultsTextBox).Text = sb.ToString(); });  
  
            this.SearchResults = resultCount;  
        }  
  
        // Call the implementation of this method in the base class.   
        // This sets the task status to complete and reports task completion.   
        base.OnStartSearch();  
    }  
    ```  
  
4.  Testez votre code.  
  
5.  Générez le projet et commencez le débogage. Dans l’instance expérimentale de Visual Studio, ouvrez la fenêtre d’outils, puis choisissez la flèche vers le bas sur le contrôle de recherche.  
  
     Le **respecter la casse** case à cocher et le **recherche uniquement les lignes paires** filtre s’affichent.  
  
6.  Choisissez le filtre.  
  
     La zone de recherche contient **lignes : « même »**, et les résultats suivants s’affichent :  
  
     bonne&2;  
  
     4 bonne  
  
     Adieu&6;  
  
7.  Supprimer `lines:"even"` dans la zone de recherche, sélectionnez le **respecter la casse** case à cocher, puis entrez `g` dans la zone de recherche.  
  
     Les résultats suivants s’affichent :  
  
     1 go  
  
     bonne&2;  
  
     Adieu&5;  
  
8.  Cliquez sur le X sur le côté droit de la zone de recherche.  
  
     La recherche est désactivée, et le contenu d’origine s’affiche. Toutefois, le **respecter la casse** est toujours activée.
