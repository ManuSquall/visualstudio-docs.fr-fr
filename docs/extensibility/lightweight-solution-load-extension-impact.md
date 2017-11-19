---
redirect_url: /visualstudio/extensibility/what-s-new-in-the-visual-studio-2017-sdk/
ms.openlocfilehash: 5706797ed88dce5b2f481b17d99e9501b960ddca
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2017
---
titre : « chargement de Solution légère (LSL) | Ms.custom de documents Microsoft » : » « ms.date : « 17/01/2017 » ms.reviewer : » « ms.suite : » « ms.technology : 
  - « vs-ide sdk » ms.tgt_pltfrm : » « ms.topic : « de l’article « helpviewer_keywords : 
  - « Charger les VSPackages, solution légère »
  - « VSPackages, rapide la charge de la solution » de ms.assetid : 0a71d91e-dc71-4d6b-bbfe-9e4ecd9e5fd1 caps.latest.revision : 1 auteur : « gregvanl » ms.author : le gestionnaire « gregvanl » : ghogen
---
# <a name="lightweight-solution-load-lsl"></a>Solution légère charge (LSL)

## <a name="background-information-on-lsl"></a>Obtenir des informations générales sur LSL

Chargement de Solution légère est une nouvelle fonctionnalité de 2017 VS qui réduit considérablement le temps de chargement de solutions, ce qui vous permet d’être plus productifs rapidement. Lorsque LSL est activée, Visual Studio entièrement ne chargera pas les projets jusqu'à ce que vous commencerez à les utiliser.

LSL peut affecter les extensions Visual Studio. Dont les fonctions dépendent d’un projet à charger les extensions ne peuvent pas de travail ou de mal fonctionner sans suivant les instructions détaillées dans ce document.

Pour plus d’informations sur LSL, utilisez les liens suivants :

* [Blog de charge de Solution légère](https://blogs.msdn.microsoft.com/visualstudio/2016/10/11/shorter-solution-load-time-in-visual-studio-15)
* Questions ? Nous contacter[lslsupport@microsoft.com](mailto:lslsupport@microsoft.com)

## <a name="enable-the-setting-to-load-projects-in-deferred-mode"></a>Activer le paramètre de charger ces projets en mode « différé »

1. Fermez toute solution actuellement ouverte.
2. Accédez à **outils** > **Option** > **projets et Solutions** > **général** paramètres page.
3. Vérifiez le **charge de la solution légère** case pour activer le paramètre.

Lorsqu’une solution est ouverte avec le paramètre ci-dessus est activé, l’IDE affiche une vue régulière des projets, mais les projets ne sont pas chargés.

## <a name="differences-between-deferred-load-and-regular-load-of-projects"></a>Différences entre le chargement différé et la charge régulière des projets

Avec une charge légère Solution, les projets ne sont pas chargés lors de l’ouverture d’une solution. Pour ces « projets différées », une hiérarchie de stub est créée. L’Explorateur de solutions affiche affichage attendu avec des icônes et les noms des projets, il n’existe aucune indication de l’interface utilisateur que certains ou tous les projets sont en « mode différé ».

Avec LSL activée, les extensions ne sont plus attendus que les projets nécessaires sont déjà entièrement chargés lorsqu’une opération est déclenchée. Les appelants doivent vérifier s’ils ont une dépendance sur les projets chargés. Si une extension requiert des informations à partir d’un projet différée, l’extension comme suit :

1. Charger l’ou les projets que nécessaire.
2. Utilisez la nouvelle **API de l’espace de travail** pour obtenir des informations à partir d’un projet différé sans son chargement.

La nouvelle **API de l’espace de travail** autoriser les extensions obtenir plus d’informations, telles que le projet propriétaire d’un fichier source et tous les fichiers sources pour un projet spécifié, à partir d’un projet différé. Dans certains cas, seul un jeu limité de projets doivent être chargés. L’option de droite est un compromis entre la fréquence des opérations, de facilité d’autres approches et l’expérience utilisateur globale.

Tous les projets et chargement solution liées toujours les événements sont déclenchés dans le mode LSL. Ainsi, les composants pour obtenir le comportement attendu à partir de Visual Studio et ils se comportent de la même manière que lorsque les projets sont chargés. Le chargement du projet liées le travail effectué au cours de la solution ouverte est considérablement réduit si.

## <a name="ui-requirements-and-changes"></a>Modifications et les spécifications de l’interface utilisateur

L’interface utilisateur doit traiter des projets chargés et différées comme égale. Cela signifie que toute action qui peut être effectuée sur un projet chargé doit être applicable aux projets différées, à quelques exceptions près. Pour des fonctions d’aide pour cela, des modifications à certaines API de la plateforme existant, ainsi que l’introduction de nouvelles API.

### <a name="expectations-for-ui"></a>Attentes en matière de l’interface utilisateur

1. Fonctionnalités doivent afficher qu'aucun élément visuel des différences selon si les projets sont chargées ou différées.
2. Toute liste ou une énumération sur des projets chargés de la solution doit inclure des projets différées.
3. Toute action disponible par rapport à un projet chargé doit être disponible pour un projet différé.
4. Fonctionnalités doit demande de chargement des projets uniquement lorsque :
  * Interaction directe de l’utilisateur avec une fonctionnalité est. Ne chargez pas projets de manière préemptive.
  * Un mouvement de « Consultez plus les résultats » est effectué par l’utilisateur. Voir ci-dessous pour cette règle de l’interface utilisateur.
  * Uniquement le projet entièrement chargé peut être utilisé pour répondre à l’action. Utilisez LSL et ouvrez API de projet chaque fois que possible et envoyer la demande de fonctionnalité demande lorsque la fonctionnalité est absente.

### <a name="changes-in-platform-apis-to-help-drive-ui"></a>Modifications dans les API qui permettent l’interface utilisateur de la plateforme

1. Nouvelles API est fournies pour demander la solution si elle a été ouverte en mode de chargement de Solution légère et combien de projets se trouvent dans un état différé.
2. Nouvel événement est fourni pour lorsque tous les projets différées sont chargés dans la solution.
3. Nouvelles API est fournies pour demander à un projet si elle est différée.
4. API existantes est mises à jour pour inclure des projets différées lors de la demande pour les projets chargés.
5. API existantes est mises à jour pour express la solution est entièrement chargée une fois la solution ouverte.

### <a name="how-to-add-see-more-results-for-a-feature"></a>Comment ajouter « Consultez plus les résultats » pour une fonctionnalité.

Les fonctions qui effectuent une requête sur le contenu des projets doivent considérer l’impact des projets différées. Dans certaines situations, fonctionnalités peuvent obtenir les résultats de leur requête LSL et API de l’espace de travail pour un projet différé. Dans d’autres cas, les limitations d’une fonctionnalité requièrent des projets à charger. Ces deux situations doivent fournir un mouvement « Voir des résultats plus » nouvelle qui permet aux utilisateurs de chargement complet des projets et la nouvelle requête. Cette opération Active les fonctionnalités afin de donner une meilleure approximation lorsqu’il existe des projets différées en donnant à l’utilisateur un moyen d’obtenir le résultat idéal lorsque les projets sont réellement chargés.

L’algorithme général pour les fonctionnalités doit être :

### <a name="when-the-query-is-performed-over-a-single-project"></a>Lorsque la requête est exécutée sur un seul projet

```csharp
// IsInDeferredState() and EnsureProjectIsLoadedHelper() in this sample can be found in the "Helpful code snippets" section of this document
public void Query(IVsHierarchy projectToQuery)
{
    // 1. Perform calculation/query
    DoQuery(projectToQuery);

    // 2. Present results to the user
    ShowResults();

    // 3. If the project was deferred, then present a "See More Results" UI element
    if (IsInDeferredState(projectToQuery))
    {
        ShowSeeMoreResults();
    }
}

public void OnClick_SeeMoreResults()
{
    // 1. Ask ask for the project to be loaded
    IVsHierarchy projectFromLastQuery = GetProjectFromLastQuery();
    IVsHierarchy loadedProject = EnsureProjectIsLoadedHelper(projectFromLastQuery);

    if (loadedProject != null)
    {
        // 2. Re-run the query on the loaded projects
        Query(loadedProject);
    }
    else
    {
        ShowErrorMessage();
    }
}
```

### <a name="when-the-query-is-performed-over-the-whole-solution"></a>Lorsque la requête est exécutée sur la Solution dans son intégralité

```csharp
// Requires Microsoft.VisualStudio.Shell.Interop.15.0.DesignTime.dll
public void Query()
{
    // 1. Perform calculation/query
    DoQuery();

    // 2. Present results to the user
    ShowResults();

    // 3. If there were deferred projects, then present a "See More Results from all projects" UI element
    var solution = // the solution
    object deferredCount = 0;
    int hr = ((IVsSolution)solution).GetProperty((int)__VSPROPID7.VSPROPID_DeferredProjectCount, out deferredCount);
    if (ErrorHandler.Succeeded(hr) && ((int)deferredCount > 0))
    {
        ShowSeeMoreResults();
    }
}

public void OnClick_SeeMoreResults()
{
    // 1. Force the solution to load, as requested by the user. This brings up a UI with a "Cancel" button (unless supppresed with __VSBSLFLAGS.VSBSLFLAGS_NotCancelable)
    var solution = // get IVsSolution4
    int hr = ((IVsSolution4)solution).EnsureSolutionIsLoaded((uint)__VSBSLFLAGS.VSBSLFLAGS_None);
    if (ErrorHandler.Succeeded(hr))
    {
        // 2. Re-run the query
        Query();
    }
    else
    {
        ShowErrorMessage();
    }
}
```

## <a name="api-changes"></a>Modifications d'API

### <a name="new-api"></a>Nouvelle API

IVsSolution7.IsSolutionLoadDeferred (out bool différée)

Retourne la valeur true si la solution en cours a été chargée en mode différé. Notez que si la solution a été chargée initialement en mode différé, même si tous les projets différées sont finalement chargé dans la session actuelle (en raison des mouvements de l’utilisateur explicite ou forcée par les opérations), cette propriété retourne toujours true.

__VSPROPID7. VSPROPID_DeferredProjectCount

Retourne le nombre de projets actuellement en mode différé. Cette propriété a une valeur dans la plage [0, VSPROPID_ProjectCount].

__VSHPROPID9. VSHPROPID_IsDeferred

Retourne la valeur true si une hiérarchie de projet est en état de chargement différé.

__VSENUMPROJFLAGS3 avec les valeurs EPF_DEFERRED et EPF_NOTDEFERRED

Ces indicateurs peuvent être passés à [IVsSolution.GetProjectEnum()](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivssolution.getprojectenum.aspx) pour itérer au sein des projets différées et non différé.

### <a name="new-events"></a>Nouveaux événements

IVsSolutionEvents7.OnAfterLoadAllDeferredProjects()

Cet événement est déclenché une fois que tous les projets différées ont été chargés. À ce stade, VSPROPID_DeferredProjectCount est égal à 0. Notez que cet événement n’est pas déclenché dans le cadre de la charge de la solution et ne peut pas être déclenché du tout dans une session. Il est déclenché uniquement si tous les projets différées sont chargés.

### <a name="changes-to-existing-api"></a>Modifications apportées aux API existantes

* Passage [__VSENUMPROJFLAGS](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.__vsenumprojflags.aspx). EPF_LOADEDINSOLUTION à [IVsSolution.GetProjectEnum()](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivssolution.getprojectenum.aspx) retourne différée des projets.
* Passage [__VSENUMPROJFLAGS](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.__vsenumprojflags.aspx). EPF_UNLOADEDINSOLUTION ne retourne pas les projets différées.
* [KnownUIContexts.SolutionExistsAndFullyLoadedContext](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.knownuicontexts.solutionexistsandfullyloadedcontext.aspx) est défini sur true sur la solution ouverte. Projets différés sont traités comme des charger de manière à ce contexte a la valeur très tôt dans le mode non-LSL.
* [__VSPROPID](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.__vspropid.aspx). VSPROPID_ProjectCount retourne la somme des projets chargés et différées.

## <a name="helpful-code-snippets"></a>Extraits de code utiles

### <a name="check-if-a-solution-was-opened-in-deferred-load-mode"></a>Vérifier si une solution a été ouvert en mode de chargement différé

```csharp
/// <summary>
/// Checks if the solution was opened in LSL mode.
/// </summary>
/// <returns>True if the solution was opened in LSL mode, false otherwise.</returns> public static bool IsSolutionLoadDeferred()
{
    IVsSolution7 vsSolution = ServiceProvider.GlobalProvider.GetService(typeof(SVsSolution)) as IVsSolution7;
    Assumes.Present(vsSolution);

    return vsSolution.IsSolutionLoadDeferred();
}
```

### <a name="check-if-a-project-is-deferred"></a>Vérifiez si un projet est différé.

```csharp
/// <summary>
/// Checks to see if a project is deferred.
/// </summary>
/// <param name="projectsToLoad">A set of deferred and/or loaded projects to ensure are loaded.</param>
/// <returns>True if the project is deferred. False if it is any other state, such as loaded, unloaded, or virtual.</returns>
/// <remarks>Requires Microsoft.VisualStudio.Shell.Interop.15.0.DesignTime.dll</remarks>
public static bool IsInDeferredState(IVsHierarchy vsHierarchy)
{
    object deferred;
    int hr = vsHierarchy.GetProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID9.VSHPROPID_IsDeferred, out deferred);

    if (ErrorHandler.Succeeded(hr))
    {
        return (bool)deferred;
    }

    return false;
}
```

### <a name="load-a-project"></a>Charger un projet

```csharp
/// <summary>
/// Ensures a project is fully loaded.
/// </summary> /// <param name="projectToLoad">A deferred or loaded project to ensure is loaded.</param>
/// <remarks>Requires Microsoft.VisualStudio.Shell.15.0.dll and Microsoft.VisualStudio.Shell.Interop.dll</remarks>
public static IVsHierarchy EnsureProjectIsLoadedHelper(IVsHierarchy projectToLoad)
{
    int hr = VSConstants.S_OK;
    var solution = // get the solution

    // 1. Ask the solution to load the required project. To reduce wait time,
    //    we load only the project we need, not the entire solution.
    hr = projectToLoad.GetGuidProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID.VSHPROPID_ProjectIDGuid, out projectGuid);
    hr = ErrorHandler.ThrowOnFailure(hr);
    hr = ((IVsSolution4)solution).EnsureProjectIsLoaded(projectGuid, (uint)__VSBSLFLAGS.VSBSLFLAGS_None);
    hr = ErrorHandler.ThrowOnFailure(hr);

    // 2. After the project is loaded, grab the latest IVsHierarchy object.
    IVsHierarchy loadedProject = null;
    hr = ((IVsSolution)solution).GetProjectOfGuid(projectGuid, out loadedProject);
    hr = ErrorHandler.ThrowOnFailure(hr);

    return loadedProject;
}
```

### <a name="load-a-set-of-projects"></a>Charger un ensemble de projets

```csharp
/// <summary>
/// Ensures a collection of IVsHierarchys are loaded. To be used when deferred projects absolutely cannot be used.
/// </summary>
/// <param name="projectsToLoad">A set of deferred and/or loaded projects to ensure are loaded.</param>
/// <remarks>Requires Microsoft.VisualStudio.Shell.15.0.dll and Microsoft.VisualStudio.Shell.Interop.dll</remarks>
public static IReadOnlyCollection<IVsHierarchy> EnsureProjectsAreLoadedHelper(IReadOnlyCollection<IVsHierarchy> projectsToLoad)
{
    if (projectsToLoad == null || projectsToLoad.Count == 0)
        return projectsToLoad;

    int hr = VSConstants.S_OK;
    List<Guid> projectGuids = new List<Guid>(projectsToLoad.Count);
    List<IVsHierarchy> loadedProjects = new List<IVsHierarchy>(projectsToLoad.Count);
    var solution = // get the solution

    // 1. Collect projects to force load
    foreach (var project in projectsToLoad)
    {
        Guid projectGuid;
        hr = project.GetGuidProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID.VSHPROPID_ProjectIDGuid, out projectGuid)
        hr = ErrorHandler.ThrowOnFailure(hr);
        projectGuids.Add(projectGuid);
    }

    // 2. Ask the solution to load the required projects. To reduce wait time,
    //    we load only the projects we need, not the entire solution.
    hr = ((IVsSolution4)solution).EnsureProjectsAreLoaded(projectCount, projectGuids.ToArray(), (uint)__VSBSLFLAGS.VSBSLFLAGS_None);
    hr = ErrorHandler.ThrowOnFailure(hr);

    // 3. After the projects are loaded, grab the latest IVsHierarchy objects
    foreach (var projectGuid in projectGuids)
    {
        IVsHierarchy loadedProject = null;
        hr = ((IVsSolution)solution).GetProjectOfGuid(projectGuid, out loadedProject);
        hr = ErrorHandler.ThrowOnFailure(hr);
        loadedProjects.Add(loadedProject);
    }

    return loadedProjects;
}
```

### <a name="checks-if-the-solution-has-deferred-projects"></a>Vérifie si la solution a différé des projets

```csharp
/// <summary>
/// Checks if the solution has deferred projects
/// </summary>
/// <returns>True if the solution has deferred projects, false otherwise.</returns>
public static bool SolutionHasDeferredProjects()
{
    IVsSolution vsSolution = ServiceProvider.GlobalProvider.GetService(typeof(SVsSolution)) as IVsSolution;
    Assumes.Present(vsSolution);
    object varHasDeferredProjects;
    if (ErrorHandler.Succeeded(vsSolution.GetProperty(
        (int)__VSPROPID7.VSPROPID_DeferredProjectCount, out varHasDeferredProjects)))
    {
        return (int)varHasDeferredProjects != 0;
    }

    return false;
}
```

## <a name="getting-detailed-information-with-workspace-apis"></a>Lors de l’obtention des informations détaillées avec les API de l’espace de travail

### <a name="how-to-get-detailed-info-on-a-lsl-solution"></a>Comment obtenir des informations détaillées sur une solution LSL

Nouvelles API de l’espace de travail sont exposés via IVsSolutionWorkspaceService pour récupérer des informations détaillées sur une solution.

Ces API peuvent être utilisées pour obtenir de l’espace de travail en cours, la solution active, les informations de ligne de commande managé, ainsi que le service d’indexation pour l’espace de travail. Ces API peut exploiter davantage le service d’indexation pour obtenir des données détaillées, par exemple, tous les fichiers sources dans un projet, le projet propriétaire d’un fichier source, tous les projets contenus dans la solution actuelle, toutes les références P2P dans un projet.

Les extraits de code suivants illustrent l’utilisation de l’API de l’espace de travail.

### <a name="get-ivssolutionworkspaceservice-initially"></a>Obtenir IVsSolutionWorkspaceService initialement

>**Remarque :** Veuillez obtenir uniquement IVsSolutionWorkspaceService dans les scénarios LSL pour éviter de charger le package de l’API de l’espace de travail.

```csharp
private readonly Lazy<IVsSolutionWorkspaceService> _solutionWorkspaceService;

[ImportingConstructor]
public DeferredProjectWorkspaceService(SVsServiceProvider serviceProvider)
{
    _solutionWorkspaceService = new Lazy<IVsSolutionWorkspaceService>(
        () => (IVsSolutionWorkspaceService)serviceProvider.GetService(typeof(SVsSolutionWorkspaceService)));
}
```

>**Remarque :** les extraits de code suivants supposent _solutionWorkspaceService est initialisé déjà tardivement.

### <a name="get-managed-command-line-info-for-deferred-projects-for-active-solution-configuration"></a>Obtenir les informations de managé de ligne de commande pour les projets différées pour la configuration de solution active

```csharp
/// <summary>
/// Get the managed command line info for active solution configuration
/// </summary>
/// <param name="cancellationToken"> the cancellation token</param>
/// <returns></returns>
public async Task<IReadOnlyDictionary<string, ManagedCommandLineInfo>> GetManagedCommandLineInfoForConfigurationAsyn(CancellationToken cancellationToken)
{
    var dte = ServiceProvider.GetGlobalService(typeof(EnvDTE.DTE)) as EnvDTE.DTE;
    var solutionConfig = (EnvDTE80.SolutionConfiguration2)dte.Solution.SolutionBuild.ActiveConfiguration;

    // Solution configuration is something like "Debug|Any CPU"
    return await _solutionWorkspaceService.Value.GetManagedCommandLineInfoAsync(
        $"{solutionConfig.Name}|{solutionConfig.PlatformName}", cancellationToken).ConfigureAwait(false);
}
```

### <a name="get-the-active-solution-file-in-lsl"></a>Obtenir le fichier de solution active dans LSL

```csharp
/// <summary>
/// Get the active solution file.
/// </summary>
/// <returns>The solution file.</returns>
public string GetActiveSolutionFile()
{
    return _solutionWorkspaceService.Value.SolutionFile;
}
```

### <a name="get-the-owning-project-of-a-source-file"></a>Obtenir le projet propriétaire d’un fichier source

```csharp
/// <summary>
/// Get the owning projects of a source file.
/// </summary>
/// <param name="filePath">the source file path.</param>
/// <returns></returns>
public async Task<IEnumerable<string>> GetOwningProjectAsync(string filePath)
{
    var workspace = _solutionWorkspaceService.Value.CurrentWorkspace;
    var indexService = workspace.GetIndexWorkspaceService();
    var result = await indexService.GetFileDependantsAsync(filePath, null, String.Empty, (int)FileReferenceInfoType.Source);
    return result.Select(f => f.Path);
}
```

### <a name="get-all-source-files-from-a-project"></a>Obtenir tous les fichiers sources à partir d’un projet

```csharp
/// <summary>
/// Get all source files from a project.
/// </summary>
/// <param name="projectFilePath">the project file path.</param>
/// <returns></returns>
public async Task<IEnumerable<string>> GetFileReferenceAsync(string projectFilePath)
{
    var workspace = _solutionWorkspaceService.Value.CurrentWorkspace;
    var indexService = workspace.GetIndexWorkspaceService();
    var fileReferenceResult = await indexService.GetFileReferencesAsync(projectFilePath, referenceTypes: (int)FileReferenceInfoType.Source);
    return fileReferenceResult.Select(f => f.Path);
}
```

### <a name="get-the-p2p-references-in-a-project"></a>Obtenir les références P2P dans un projet

```csharp
/// <summary>
/// Get outputs of project.
/// </summary>
/// <param name="projectFilePath">the project file path.</param>
/// <returns></returns>
public async Task<IEnumerable<string>> GetFileReferenceAsync(string projectFilePath)
{
    var workspace = _solutionWorkspaceService.Value.CurrentWorkspace;
    var indexService = workspace.GetIndexWorkspaceService();
    var fileReferenceResult = await indexService.GetFileReferencesAsync(projectFilePath, context: "Debug|AnyCPU", referenceTypes: (int)FileReferenceInfoType.Output);
    return fileReferenceResult.Select(f => f.Path);
}
```

### <a name="get-all-the-projects-in-a-solution"></a>Obtenir tous les projets dans une solution

```csharp
/// <summary>
/// Get the projects in a solution.
/// </summary>
/// <param name="solutionFilePath">the solution file path.</param>
/// <returns></returns>
public async Task<IEnumerable<string>> GetProjectsInSolutionAsync(string solutionFilePath)
{
    var workspace = _solutionWorkspaceService.Value.CurrentWorkspace;
    var indexService = workspace.GetIndexWorkspaceService();

    // Passing the configuration|Platform that projects apply to; passing null will return projects with all configurations.
    var result = await indexService.GetFileReferencesAsync(solutionFilePath, context: "Debug|AnyCPU", referenceTypes: (int)FileReferenceInfoType.ProjectReference);
    return result.Select(f => f.Path);
}
```

## <a name="troubleshooting"></a>Résolution des problèmes

En raison de la nature de LSL, il est intentionnel que les utilisateurs ne peuvent pas voir une différence entre les projets chargés et différées. Cela peut compliquer fonctionnalité développement et test.

Vous pouvez activer les indications visuelles dans l’interface utilisateur pour les projets différées en procédant comme suit :

1. Fermez Visual Studio.
2. Regedit.exe
3. Sélectionnez HKLM
4. Fichier > charger la ruche
5. `%localappdata%\microsoft\visualstudio\15.0_<instance ID>\privateregistry.bin`
6. Entrez « VisualStudio » sous la forme d’un nom de clé
7. Définissez `HKLM\VisualStudio\Software\Microsoft\VisualStudio\15.0_<instanceID>\FeatureFlags\Solution\Loading\Deferred\Hint\Value=1` (DWORD)
8. Sélectionnez HKLM\VisualStudio
9. Fichier > décharger la ruche
10. Démarrez Visual Studio

Pour d’autres questions, veuillez contacter [ lslsupport@microsoft.com ](mailto:lslsupport@microsoft.com).






