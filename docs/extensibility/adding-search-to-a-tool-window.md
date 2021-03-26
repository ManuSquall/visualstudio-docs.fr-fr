---
title: Ajout d’une recherche à une fenêtre outil | Microsoft Docs
description: Découvrez comment ajouter une fonctionnalité de recherche, notamment une zone de recherche, un filtrage et un indicateur de progression, à une fenêtre outil dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- tool windows, adding search
ms.assetid: f78c4892-8060-49c4-8ecd-4360f1b4d133
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 82176afaacae3b9f4553c8b1b5b41b9a4f10dace
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105097550"
---
# <a name="add-search-to-a-tool-window"></a>Ajouter une recherche à une fenêtre outil
Lorsque vous créez ou mettez à jour une fenêtre outil dans votre extension, vous pouvez ajouter la même fonctionnalité de recherche qui apparaît ailleurs dans Visual Studio. Cette fonctionnalité comprend les fonctionnalités suivantes :

- Zone de recherche qui se trouve toujours dans une zone personnalisée de la barre d’outils.

- Indicateur de progression qui est superposé sur la zone de recherche elle-même.

- La possibilité d’afficher les résultats dès que vous entrez chaque caractère (recherche instantanée) ou uniquement après avoir choisi la touche **entrée** (Rechercher à la demande).

- Liste qui indique les termes pour lesquels vous avez effectué la recherche la plus récente.

- Possibilité de filtrer les recherches en fonction de champs ou d’aspects spécifiques des cibles de recherche.

En suivant cette procédure pas à pas, vous allez apprendre à effectuer les tâches suivantes :

1. Créez un projet VSPackage.

2. Créez une fenêtre outil qui contient un UserControl avec une zone de texte en lecture seule.

3. Ajoutez une zone de recherche à la fenêtre outil.

4. Ajoutez l’implémentation de la recherche.

5. Activez la recherche instantanée et l’affichage d’une barre de progression.

6. Ajoutez une option **respecter la casse** .

7. Ajoutez un filtre **lignes de recherche uniquement** .

## <a name="to-create-a-vsix-project"></a>Pour créer un projet VSIX

1. Créez un projet VSIX nommé `TestToolWindowSearch` à l’aide d’une fenêtre outil nommée **TestSearch**. Si vous avez besoin d’aide pour ce faire, consultez [création d’une extension avec une fenêtre outil](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="to-create-a-tool-window"></a>Pour créer une fenêtre outil

1. Dans le `TestToolWindowSearch` projet, ouvrez le fichier *TestSearchControl. Xaml* .

2. Remplacez le `<StackPanel>` bloc existant par le bloc suivant, qui ajoute un en lecture seule <xref:System.Windows.Controls.TextBox> au <xref:System.Windows.Controls.UserControl> dans la fenêtre outil.

    ```xaml
    <StackPanel Orientation="Vertical">
        <TextBox Name="resultsTextBox" Height="800.0"
            Width="800.0"
            IsReadOnly="True">
        </TextBox>
    </StackPanel>
    ```

3. Dans le fichier *TestSearchControl. Xaml. cs* , ajoutez la directive using suivante :

    ```csharp
    using System.Text;
    ```

4. Supprimez la `button1_Click()` méthode.

     Dans la classe **TestSearchControl** , ajoutez le code suivant.

     Ce code ajoute une <xref:System.Windows.Controls.TextBox> propriété publique nommée **SearchResultsTextBox** et une propriété de chaîne publique nommée **SearchContent**. Dans le constructeur, SearchResultsTextBox a la valeur de la zone de texte et SearchContent est initialisé à un ensemble de chaînes délimitées par des sauts de ligne. Le contenu de la zone de texte est également initialisé sur le jeu de chaînes.

     [!code-csharp[ToolWindowSearch#1](../extensibility/codesnippet/CSharp/adding-search-to-a-tool-window_1.cs)]
     [!code-vb[ToolWindowSearch#1](../extensibility/codesnippet/VisualBasic/adding-search-to-a-tool-window_1.vb)]

5. Générez le projet et commencez le débogage. L’instance expérimentale de Visual Studio s’affiche.

6. Dans la barre de menus, choisissez **Afficher**  >  **autres fenêtres**  >  **TestSearch**.

     La fenêtre outil s’affiche, mais le contrôle de recherche n’apparaît pas encore.

## <a name="to-add-a-search-box-to-the-tool-window"></a>Pour ajouter une zone de recherche à la fenêtre outil

1. Dans le fichier *TestSearch. cs* , ajoutez le code suivant à la `TestSearch` classe. Le code substitue la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> propriété afin que l’accesseur Get retourne `true` .

     Pour activer la recherche, vous devez substituer la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> propriété. La <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> classe implémente <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch> et fournit une implémentation par défaut qui n’active pas la recherche.

    ```csharp
    public override bool SearchEnabled
    {
        get { return true; }
    }
    ```

2. Générez le projet et commencez le débogage. L’instance expérimentale s’affiche.

3. Dans l’instance expérimentale de Visual Studio, ouvrez **TestSearch**.

     En haut de la fenêtre outil, un contrôle de recherche s’affiche avec un filigrane de **recherche** et une icône de loupe. Toutefois, la recherche ne fonctionne pas encore, car le processus de recherche n’a pas été implémenté.

## <a name="to-add-the-search-implementation"></a>Pour ajouter l’implémentation de la recherche
 Lorsque vous activez la recherche sur un <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> , comme dans la procédure précédente, la fenêtre outil crée un hôte de recherche. Cet hôte configure et gère les processus de recherche, qui se produisent toujours sur un thread d’arrière-plan. Étant donné que la <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> classe gère la création de l’hôte de recherche et la configuration de la recherche, il vous suffit de créer une tâche de recherche et de fournir la méthode de recherche. Le processus de recherche se produit sur un thread d’arrière-plan et les appels au contrôle de fenêtre outil se produisent sur le thread d’interface utilisateur. Par conséquent, vous devez utiliser la méthode [ThreadHelper. Invoke *](https://msdn.microsoft.com/data/ee197798(v=vs.85)) pour gérer les appels que vous effectuez dans le traitement du contrôle.

1. Dans le fichier *TestSearch. cs* , ajoutez les `using` directives suivantes :

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

2. Dans la `TestSearch` classe, ajoutez le code suivant, qui effectue les actions suivantes :

    - Substitue la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> méthode pour créer une tâche de recherche.

    - Substitue la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> méthode pour restaurer l’état de la zone de texte. Cette méthode est appelée lorsqu’un utilisateur annule une tâche de recherche et lorsqu’un utilisateur définit ou désdéfinit des options ou des filtres. <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A>Et <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> sont appelés sur le thread d’interface utilisateur. Par conséquent, vous n’avez pas besoin d’accéder à la zone de texte à l’aide de la méthode [ThreadHelper. Invoke *](https://msdn.microsoft.com/data/ee197798(v=vs.85)) .

    - Crée une classe nommée `TestSearchTask` qui hérite de <xref:Microsoft.VisualStudio.Shell.VsSearchTask> , qui fournit une implémentation par défaut de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSearchTask> .

         Dans `TestSearchTask` , le constructeur définit un champ privé qui fait référence à la fenêtre outil. Pour fournir la méthode de recherche, vous devez substituer les <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStopSearch%2A> méthodes et. La <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> méthode est l’emplacement où vous implémentez le processus de recherche. Ce processus comprend l’exécution de la recherche, l’affichage des résultats de la recherche dans la zone de texte et l’appel de l’implémentation de la classe de base de cette méthode pour signaler que la recherche est terminée.

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

3. Testez votre implémentation de la recherche en procédant comme suit :

    1. Régénérez le projet et démarrez le débogage.

    2. Dans l’instance expérimentale de Visual Studio, ouvrez à nouveau la fenêtre outil, entrez un texte à rechercher dans la fenêtre de recherche, puis cliquez sur **entrée**.

         Les résultats corrects doivent s’afficher.

## <a name="to-customize-the-search-behavior"></a>Pour personnaliser le comportement de recherche
 En modifiant les paramètres de recherche, vous pouvez apporter différentes modifications à l’apparence du contrôle de recherche et à la façon dont la recherche est effectuée. Par exemple, vous pouvez modifier le filigrane (le texte par défaut qui apparaît dans la zone de recherche), la largeur minimale et la largeur maximale du contrôle de recherche, et s’il faut afficher une barre de progression. Vous pouvez également modifier le point auquel les résultats de la recherche s’affichent (à la demande ou la recherche instantanée) et s’il faut afficher une liste des termes pour lesquels vous avez récemment effectué une recherche. Vous pouvez trouver la liste complète des paramètres dans la <xref:Microsoft.VisualStudio.PlatformUI.SearchSettingsDataSource> classe.

1. Dans le fichier * TestSearch. cs *, ajoutez le code suivant à la `TestSearch` classe. Ce code active la recherche instantanée plutôt que la recherche à la demande (ce qui signifie que l’utilisateur n’a pas besoin de cliquer sur **entrée**). Le code substitue la `ProvideSearchSettings` méthode dans la `TestSearch` classe, ce qui est nécessaire pour modifier les paramètres par défaut.

    ```csharp
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)
    {
        Utilities.SetValue(pSearchSettings,
            SearchSettingsDataSource.SearchStartTypeProperty.Name,
            (uint)VSSEARCHSTARTTYPE.SST_INSTANT);}
    ```

2. Testez le nouveau paramètre en reconstruisant la solution et en redémarrant le débogueur.

     Les résultats de la recherche s’affichent chaque fois que vous entrez un caractère dans la zone de recherche.

3. Dans la `ProvideSearchSettings` méthode, ajoutez la ligne suivante, qui active l’affichage d’une barre de progression.

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

     Pour que la barre de progression s’affiche, la progression doit être signalée. Pour signaler la progression, supprimez les marques de commentaire du code suivant dans la `OnStartSearch` méthode de la `TestSearchTask` classe :

    ```csharp
    SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));
    ```

4. Pour ralentir le traitement de l’affichage de la barre de progression, supprimez les marques de commentaire de la ligne suivante dans la `OnStartSearch` méthode de la `TestSearchTask` classe :

    ```csharp
    System.Threading.Thread.Sleep(100);
    ```

5. Testez les nouveaux paramètres en reconstruisant la solution et en commençant au débogage.

     La barre de progression s’affiche dans la fenêtre de recherche (sous la forme d’une ligne bleue sous la zone de texte Rechercher) chaque fois que vous effectuez une recherche.

## <a name="to-enable-users-to-refine-their-searches"></a>Pour permettre aux utilisateurs d’affiner leurs recherches
 Vous pouvez autoriser les utilisateurs à affiner leurs recherches à l’aide d’options telles que **respecter la casse** ou **mot entier**. Les options peuvent être booléennes, qui apparaissent sous la forme de cases à cocher, ou de commandes, qui s’affichent sous forme de boutons. Pour cette procédure pas à pas, vous allez créer une option booléenne.

1. Dans le fichier *TestSearch. cs* , ajoutez le code suivant à la `TestSearch` classe. Le code substitue la `SearchOptionsEnum` méthode, ce qui permet à l’implémentation de recherche de détecter si une option donnée est activée ou désactivée. Le code dans `SearchOptionsEnum` ajoute une option pour faire correspondre la casse à un <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumWindowSearchOptions> énumérateur. L’option permettant de respecter la casse est également rendue disponible en tant que `MatchCaseOption` propriété.

    ```csharp
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

2. Dans la `TestSearchTask` classe, supprimez les marques de commentaire de la ligne suivante dans la `OnStartSearch` méthode :

    ```csharp
    matchCase = m_toolWindow.MatchCaseOption.Value;
    ```

3. Testez l’option :

    1. Générez le projet et commencez le débogage. L’instance expérimentale s’affiche.

    2. Dans la fenêtre outil, choisissez la flèche bas sur le côté droit de la zone de texte.

         La case à cocher **respecter la casse** s’affiche.

    3. Activez la case à cocher **respecter la casse** , puis effectuez des recherches.

## <a name="to-add-a-search-filter"></a>Pour ajouter un filtre de recherche
 Vous pouvez ajouter des filtres de recherche qui permettent aux utilisateurs d’affiner l’ensemble des cibles de recherche. Par exemple, vous pouvez filtrer les fichiers dans l’Explorateur de fichiers en fonction des dates auxquelles ils ont été modifiés en dernier et de leurs extensions de nom de fichier. Dans cette procédure pas à pas, vous allez ajouter un filtre pour les lignes paires uniquement. Lorsque l’utilisateur choisit ce filtre, l’hôte de recherche ajoute les chaînes que vous spécifiez à la requête de recherche. Vous pouvez ensuite identifier ces chaînes à l’intérieur de votre méthode de recherche et filtrer les cibles de recherche en conséquence.

1. Dans le fichier *TestSearch. cs* , ajoutez le code suivant à la `TestSearch` classe. Le code implémente `SearchFiltersEnum` en ajoutant un <xref:Microsoft.VisualStudio.PlatformUI.WindowSearchSimpleFilter> qui spécifie de filtrer les résultats de la recherche afin que seules les lignes paires apparaissent.

    ```csharp
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

     Le contrôle de recherche affiche maintenant le filtre de recherche `Search even lines only` . Lorsque l’utilisateur choisit le filtre, la chaîne `lines:"even"` apparaît dans la zone de recherche. D’autres critères de recherche peuvent apparaître en même temps que le filtre. Les chaînes de recherche peuvent apparaître avant le filtre, après le filtre, ou les deux.

2. Dans le fichier *TestSearch. cs* , ajoutez les méthodes suivantes à la `TestSearchTask` classe, qui se trouve dans la `TestSearch` classe. Ces méthodes prennent en charge la `OnStartSearch` méthode, que vous allez modifier à l’étape suivante.

    ```csharp
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

3. Dans la `TestSearchTask` classe, mettez à jour la `OnStartSearch` méthode avec le code suivant. Cette modification met à jour le code pour prendre en charge le filtre.

    ```csharp
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

4. Testez votre code.

5. Générez le projet et commencez le débogage. Dans l’instance expérimentale de Visual Studio, ouvrez la fenêtre outil, puis choisissez la flèche vers le bas sur le contrôle de recherche.

     La case à cocher **respecter la casse** et le filtre **Rechercher les lignes paires uniquement** s’affichent.

6. Choisissez le filtre.

     La zone de recherche contient des **lignes : « pair »** et les résultats suivants s’affichent :

     2 bonne

     4 bonne

     6 Adieu

7. Supprimer `lines:"even"` dans la zone de recherche, activez la case à cocher **respecter la casse** , puis entrez `g` dans la zone de recherche.

     Les résultats suivants s’affichent :

     1 Go

     2 bonne

     5 adieu

8. Choisissez le X sur le côté droit de la zone de recherche.

     La recherche est désactivée et le contenu d’origine s’affiche. Toutefois, la case à cocher **respecter la casse** est toujours activée.
