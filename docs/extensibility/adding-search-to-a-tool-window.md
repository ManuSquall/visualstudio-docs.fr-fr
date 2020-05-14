---
title: Ajout de la recherche à une fenêtre d’outil (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, adding search
ms.assetid: f78c4892-8060-49c4-8ecd-4360f1b4d133
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f9112a3368ba604c4291f9018e763022e953c4fc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740139"
---
# <a name="add-search-to-a-tool-window"></a>Ajouter la recherche à une fenêtre d’outil
Lorsque vous créez ou mettez à jour une fenêtre d’outil dans votre extension, vous pouvez ajouter la même fonctionnalité de recherche qui apparaît ailleurs dans Visual Studio. Cette fonctionnalité comprend les fonctionnalités suivantes :

- Une boîte de recherche qui est toujours située dans une zone personnalisée de la barre d’outils.

- Un indicateur de progression qui est superposé sur la boîte de recherche elle-même.

- La possibilité d’afficher les résultats dès que vous entrez chaque personnage (recherche instantanée) ou seulement après avoir choisi la clé **Enter** (recherche sur demande).

- Une liste qui affiche les termes pour lesquels vous avez cherché plus récemment.

- La possibilité de filtrer les recherches par des champs spécifiques ou des aspects des cibles de recherche.

En suivant cette procédure pas à pas, vous apprendrez à effectuer les tâches suivantes :

1. Créez un projet VSPackage.

2. Créez une fenêtre d’outils qui contient un userControl avec une TextBox lue uniquement.

3. Ajoutez une boîte de recherche à la fenêtre de l’outil.

4. Ajouter l’implémentation de recherche.

5. Activez la recherche et l’affichage instantanés d’une barre de progression.

6. Ajouter une option **de cas de match.**

7. Ajoutez un filtre De recherche même que des **lignes.**

## <a name="to-create-a-vsix-project"></a>Pour créer un projet VSIX

1. Créez un projet `TestToolWindowSearch` VSIX nommé avec une fenêtre d’outils nommée **TestSearch**. Si vous avez besoin d’aide pour ce faire, voir [Créer une extension avec une fenêtre d’outil](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="to-create-a-tool-window"></a>Pour créer une fenêtre d’outils

1. Dans `TestToolWindowSearch` le projet, ouvrez le fichier *TestSearchControl.xaml.*

2. Remplacez `<StackPanel>` le bloc existant par le bloc <xref:System.Windows.Controls.TextBox> suivant, <xref:System.Windows.Controls.UserControl> qui ajoute une lecture seulement à la fenêtre de l’outil.

    ```xaml
    <StackPanel Orientation="Vertical">
        <TextBox Name="resultsTextBox" Height="800.0"
            Width="800.0"
            IsReadOnly="True">
        </TextBox>
    </StackPanel>
    ```

3. Dans le fichier *TestSearchControl.xaml.cs,* ajoutez la directive suivante à l’aide :

    ```csharp
    using System.Text;
    ```

4. Retirez `button1_Click()` la méthode.

     Dans la classe **TestSearchControl,** ajoutez le code suivant.

     Ce code ajoute <xref:System.Windows.Controls.TextBox> une propriété publique nommée **SearchResultsTextBox** et une propriété à cordes publiques nommée **SearchContent**. Dans le constructeur, SearchResultsTextBox est réglé sur la boîte de texte, et SearchContent est paralé à un nouvel ensemble de cordes délimitées. Le contenu de la boîte à texte est également parasémenté à l’ensemble des cordes.

     [!code-csharp[ToolWindowSearch#1](../extensibility/codesnippet/CSharp/adding-search-to-a-tool-window_1.cs)]
     [!code-vb[ToolWindowSearch#1](../extensibility/codesnippet/VisualBasic/adding-search-to-a-tool-window_1.vb)]

5. Générez le projet et commencez le débogage. L’exemple expérimental de Visual Studio apparaît.

6. Sur la barre de menu, choisissez **Voir** > **d’autres** > **TestSearch**Windows .

     La fenêtre de l’outil apparaît, mais le contrôle de recherche n’apparaît pas encore.

## <a name="to-add-a-search-box-to-the-tool-window"></a>Pour ajouter une boîte de recherche à la fenêtre d’outil

1. Dans le *fichier TestSearch.cs,* ajoutez le `TestSearch` code suivant à la classe. Le code remplace <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> la propriété de sorte `true`que l’accesseur obtenir des retours .

     Pour activer la recherche, <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> vous devez passer outre à la propriété. La <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> classe <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch> implémente et fournit une implémentation par défaut qui n’active pas la recherche.

    ```csharp
    public override bool SearchEnabled
    {
        get { return true; }
    }
    ```

2. Générez le projet et commencez le débogage. L’instance expérimentale apparaît.

3. Dans l’exemple expérimental de Visual Studio, ouvert **TestSearch**.

     En haut de la fenêtre d’outil, un contrôle de recherche apparaît avec un filigrane **de recherche** et une icône de loupe. Cependant, la recherche ne fonctionne pas encore parce que le processus de recherche n’a pas été mis en œuvre.

## <a name="to-add-the-search-implementation"></a>Pour ajouter la mise en œuvre de recherche
 Lorsque vous activez <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>la recherche sur un , comme dans la procédure précédente, la fenêtre d’outil crée un hôte de recherche. Cet hôte met en place et gère les processus de recherche, qui se produisent toujours sur un thread de fond. Étant <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> donné que la classe gère la création de l’hôte de recherche et la mise en place de la recherche, vous n’avez qu’à créer une tâche de recherche et à fournir la méthode de recherche. Le processus de recherche se produit sur un thread de fond, et les appels vers le contrôle de fenêtre d’outil se produisent sur le thread d’interface utilisateur. Par conséquent, vous devez utiliser la méthode [ThreadHelper.InvokeMD](https://msdn.microsoft.com/data/ee197798(v=vs.85)) pour gérer tous les appels que vous faites pour traiter le contrôle.

1. Dans le fichier *TestSearch.cs,* ajoutez `using` les directives suivantes :

    ```csharp
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

2. Dans `TestSearch` la classe, ajoutez le code suivant, qui effectue les actions suivantes :

    - Remplace la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> méthode pour créer une tâche de recherche.

    - Remplace la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> méthode pour restaurer l’état de la boîte à texte. Cette méthode s’appelle lorsqu’un utilisateur annule une tâche de recherche et lorsqu’un utilisateur définit ou désélement des options ou des filtres. Les <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> deux et sont appelés sur le fil d’interface utilisateur. Par conséquent, vous n’avez pas besoin d’accéder à la boîte de texte au moyen de la méthode [ThreadHelper.Invoke.](https://msdn.microsoft.com/data/ee197798(v=vs.85))

    - Crée une classe qui `TestSearchTask` est nommé <xref:Microsoft.VisualStudio.Shell.VsSearchTask>qui hérite de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSearchTask>, qui fournit une mise en œuvre par défaut de .

         Dans `TestSearchTask`, le constructeur définit un champ privé qui fait référence à la fenêtre d’outil. Pour fournir la méthode de <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> recherche, vous remplacez les méthodes et <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStopSearch%2A> les méthodes. La <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> méthode est l’endroit où vous implémentez le processus de recherche. Ce processus comprend l’exécution de la recherche, l’affichage des résultats de recherche dans la boîte de texte, et d’appeler la mise en œuvre de la classe de base de cette méthode pour signaler que la recherche est terminée.

    ```csharp
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

3. Testez votre implémentation de recherche en effectuant les étapes suivantes :

    1. Reconstruire le projet et commencer à débogage.

    2. Dans le cas expérimental de Visual Studio, ouvrez à nouveau la fenêtre de l’outil, entrez un texte de recherche dans la fenêtre de recherche et cliquez sur **ENTER**.

         Les bons résultats doivent apparaître.

## <a name="to-customize-the-search-behavior"></a>Personnaliser le comportement de recherche
 En modifiant les paramètres de recherche, vous pouvez apporter une variété de modifications dans la façon dont le contrôle de recherche apparaît et comment la recherche est effectuée. Par exemple, vous pouvez modifier le filigrane (le texte par défaut qui apparaît dans la boîte de recherche), la largeur minimale et maximale du contrôle de recherche, et s’il convient d’afficher une barre de progression. Vous pouvez également modifier le point où les résultats de recherche commencent à apparaître (sur demande ou recherche instantanée) et s’il faut afficher une liste de termes pour lesquels vous avez récemment cherché. Vous pouvez trouver la liste <xref:Microsoft.VisualStudio.PlatformUI.SearchSettingsDataSource> complète des paramètres de la classe.

1. Dans le fichier TestSearch.csMD, ajoutez le code `TestSearch` suivant à la classe. Ce code permet une recherche instantanée au lieu d’une recherche à la demande (ce qui signifie que l’utilisateur n’a pas à cliquer sur **ENTER**). Le code remplace `ProvideSearchSettings` la méthode `TestSearch` de la classe, qui est nécessaire pour modifier les paramètres par défaut.

    ```csharp
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)
    {
        Utilities.SetValue(pSearchSettings,
            SearchSettingsDataSource.SearchStartTypeProperty.Name,
            (uint)VSSEARCHSTARTTYPE.SST_INSTANT);}
    ```

2. Testez le nouveau paramètre en reconstruisant la solution et en redémarrant le débbuggeur.

     Les résultats de recherche apparaissent chaque fois que vous entrez un personnage dans la boîte de recherche.

3. Dans `ProvideSearchSettings` la méthode, ajouter la ligne suivante, ce qui permet l’affichage d’une barre de progression.

    ```csharp
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

     Pour que la barre de progression apparaisse, les progrès doivent être signalés. Pour signaler les progrès, désengagez `OnStartSearch` le `TestSearchTask` code suivant dans la méthode de la classe :

    ```csharp
    SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));
    ```

4. Pour ralentir suffisamment le traitement que la barre de progression `OnStartSearch` est `TestSearchTask` visible, désengagez la ligne suivante dans la méthode de la classe :

    ```csharp
    System.Threading.Thread.Sleep(100);
    ```

5. Testez les nouveaux paramètres en reconstruisant la solution et en commençant à déboiffer.

     La barre de progression apparaît dans la fenêtre de recherche (comme une ligne bleue en dessous de la boîte de texte de recherche) chaque fois que vous effectuez une recherche.

## <a name="to-enable-users-to-refine-their-searches"></a>Permettre aux utilisateurs d’affiner leurs recherches
 Vous pouvez permettre aux utilisateurs d’affiner leurs recherches au moyen d’options telles que **l’affaire Match** ou **Match mot entier**. Les options peuvent être boolean, qui apparaissent sous forme de cases à cocher, ou commandes, qui apparaissent sous forme de boutons. Pour cette procédure pas à pas, vous allez créer une option boolean.

1. Dans le *fichier TestSearch.cs,* ajoutez le `TestSearch` code suivant à la classe. Le code remplace `SearchOptionsEnum` la méthode, qui permet à la mise en œuvre de recherche de détecter si une option donnée est allumée ou éteinte. Le code `SearchOptionsEnum` ajoute une option pour <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumWindowSearchOptions> assortir le cas à un enumérateur. L’option de jumeler cas `MatchCaseOption` est également mis à disposition comme la propriété.

    ```csharp
    private IVsEnumWindowSearchOptions m_optionsEnum;
    public override IVsEnumWindowSearchOptions SearchOptionsEnum
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

2. Dans `TestSearchTask` la classe, désengagez `OnStartSearch` la ligne suivante dans la méthode :

    ```csharp
    matchCase = m_toolWindow.MatchCaseOption.Value;
    ```

3. Testez l’option :

    1. Générez le projet et commencez le débogage. L’instance expérimentale apparaît.

    2. Dans la fenêtre de l’outil, choisissez la flèche Down sur le côté droit de la boîte de texte.

         La case **Match** est apparue.

    3. Sélectionnez la case **Match,** puis effectuez quelques recherches.

## <a name="to-add-a-search-filter"></a>Pour ajouter un filtre de recherche
 Vous pouvez ajouter des filtres de recherche qui permettent aux utilisateurs d’affiner l’ensemble des objectifs de recherche. Par exemple, vous pouvez filtrer les fichiers dans File Explorer par les dates auxquelles ils ont été modifiés plus récemment et leurs extensions de nom de fichier. Dans cette procédure pas à pas, vous ajouterez un filtre pour les lignes égales seulement. Lorsque l’utilisateur choisit ce filtre, l’hôte de recherche ajoute les chaînes que vous spécifiez à la requête de recherche. Vous pouvez ensuite identifier ces chaînes à l’intérieur de votre méthode de recherche et filtrer les cibles de recherche en conséquence.

1. Dans le *fichier TestSearch.cs,* ajoutez le `TestSearch` code suivant à la classe. Le code `SearchFiltersEnum` implémente en ajoutant un <xref:Microsoft.VisualStudio.PlatformUI.WindowSearchSimpleFilter> qui spécifie pour filtrer les résultats de recherche de sorte que seules les lignes apparaissent.

    ```csharp
    public override IVsEnumWindowSearchFilters SearchFiltersEnum
    {
        get
        {
            List<IVsWindowSearchFilter> list = new List<IVsWindowSearchFilter>();
            list.Add(new WindowSearchSimpleFilter("Search even lines only", "Search even lines only", "lines", "even"));
            return new WindowSearchFilterEnumerator(list) as IVsEnumWindowSearchFilters;
        }
    }

    ```

     Maintenant, le contrôle de `Search even lines only`recherche affiche le filtre de recherche . Lorsque l’utilisateur choisit le `lines:"even"` filtre, la chaîne apparaît dans la boîte de recherche. D’autres critères de recherche peuvent apparaître en même temps que le filtre. Les chaînes de recherche peuvent apparaître avant le filtre, après le filtre, ou les deux.

2. Dans le *fichier TestSearch.cs,* ajoutez les méthodes `TestSearchTask` suivantes à la `TestSearch` classe, qui est dans la classe. Ces méthodes `OnStartSearch` prennent en charge la méthode, que vous modifierez à l’étape suivante.

    ```csharp
    private string RemoveFromString(string origString, string stringToRemove)
    {
        int index = origString.IndexOf(stringToRemove);
        if (index == -1)
            return origString;
        else 
             return (origString.Substring(0, index) + origString.Substring(index + stringToRemove.Length)).Trim();
    }

    private string[] GetEvenItems(string[] contentArr)
    {
        int length = contentArr.Length / 2;
        string[] evenContentArr = new string[length];

        int indexB = 0;
        for (int index = 1; index < contentArr.Length; index += 2)
        {
            evenContentArr[indexB] = contentArr[index];
            indexB++;
        }

        return evenContentArr;
    }
    ```

3. Dans `TestSearchTask` la classe, `OnStartSearch` mettre à jour la méthode avec le code suivant. Cette modification met à jour le code pour prendre en charge le filtre.

    ```csharp
    protected override void OnStartSearch()
    {
        // Use the original content of the text box as the target of the search. 
        var separator = new string[] { Environment.NewLine };
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

4. Testez votre code.

5. Générez le projet et commencez le débogage. Dans le cas expérimental de Visual Studio, ouvrez la fenêtre de l’outil, puis choisissez la flèche Down sur le contrôle de recherche.

     La case **Match** et les **lignes de recherche même filtrent uniquement** apparaissent.

6. Choisissez le filtre.

     La boîte de recherche contient des **lignes: "même"**, et les résultats suivants apparaissent:

     2 bonnes

     4 Bon

     6 Au revoir

7. Supprimer `lines:"even"` de la boîte de recherche, sélectionner la `g` case **Match,** puis entrer dans la boîte de recherche.

     Les résultats suivants apparaissent :

     1 aller

     2 bonnes

     5 au revoir

8. Choisissez le X sur le côté droit de la boîte de recherche.

     La recherche est effacée, et le contenu d’origine apparaît. Toutefois, la case **Case** Check est toujours sélectionnée.
