---
title: Propriétés communes des projets MSBuild | Microsoft Docs
ms.date: 01/18/2018
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- msbuild, common properties
- msbuild, project file properties
- ExcludeDeploymentUrl property
- project file properties (MSBuild)
ms.assetid: 9857505d-ae15-42f1-936d-6cd7fb9dd276
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 56b6890733d00fb650ea611e759c8f8d6a9b2bc5
ms.sourcegitcommit: 0ef51e3517436a85cfb85bf492722d566ce602c4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2019
ms.locfileid: "65934524"
---
# <a name="common-msbuild-project-properties"></a>Propriétés communes des projets MSBuild
Le tableau ci-dessous répertorie les propriétés fréquemment utilisées qui sont définies dans les fichiers projet Visual Studio ou incluses dans les fichiers *.targets* fournis par MSBuild.

 Les fichiers projet dans Visual Studio (*.csproj*, *.vbproj*, *.vcxproj* et autres) contiennent le code XML MSBuild qui s’exécute quand vous générez un projet à l’aide de l’IDE. Les projets importent généralement un ou plusieurs fichiers *.targets* pour définir leur processus de génération. Pour plus d’informations, consultez [Fichiers .targets MSBuild](../msbuild/msbuild-dot-targets-files.md).

## <a name="list-of-common-properties-and-parameters"></a>Liste des propriétés et paramètres courants

| Nom de propriété ou de paramètre | Description |
|------------------------------------| - |
| AdditionalLibPaths | Spécifie des dossiers supplémentaires dans lesquels les compilateurs doivent rechercher des assemblys de référence. |
| AddModules | Entraîne la mise à disposition par le compilateur de toutes les informations de type à partir des fichiers spécifiés, pour le projet en cours de compilation. Cette propriété est équivalente au commutateur `/addModules` du compilateur. |
| ALToolPath | Chemin du fichier *AL.exe*. Cette propriété remplace la version actuelle du fichier *AL.exe* pour permettre l’utilisation d’une autre version. |
| ApplicationIcon | Fichier icône *.ico* à passer au compilateur pour qu’il soit incorporé en tant qu’icône Win32. Cette propriété est équivalente au commutateur `/win32icon` du compilateur. |
| ApplicationManifest | Spécifie le chemin d'accès du fichier utilisé pour générer les informations de manifeste de Contrôle de compte d'utilisateur externe. S'applique uniquement aux projets Visual Studio ciblant [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)].<br /><br /> Dans la plupart des cas, le manifeste est incorporé. Toutefois, si vous utilisez un déploiement COM sans inscription ou [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], le manifeste peut être un fichier externe installé avec les assemblys de votre application. Pour plus d'informations, consultez la propriété NoWin32Manifest dans cette rubrique. |
| AssemblyOriginatorKeyFile | Spécifie le fichier utilisé pour signer l’assembly (*.snk* ou *.pfx*) et passé à la [tâche ResolveKeySource](../msbuild/resolvekeysource-task.md) pour générer la clé réelle utilisée pour signer l’assembly. |
| AssemblySearchPaths | Liste d'emplacements dans lesquels il convient de rechercher au cours de la résolution de l'assembly de référence au moment de la génération. L'ordre dans lequel les chemins d'accès apparaissent dans cette liste est significatif, car les chemins répertoriés antérieurement ont priorité sur les entrées ultérieures. |
| AssemblyName | Nom de l'assembly de sortie définitif après génération du projet. |
| BaseAddress | Spécifie l'adresse de base de l'assembly de sortie principal. Cette propriété est équivalente au commutateur `/baseaddress` du compilateur. |
| BaseOutputPath | Spécifie le chemin d'accès de base du fichier de sortie. S'il est défini, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] utilise `OutputPath = $(BaseOutputPath)\$(Configuration)\`. Exemple de syntaxe : `<BaseOutputPath>c:\xyz\bin\</BaseOutputPath>` |
| BaseIntermediateOutputPath | Dossier de niveau supérieur dans lequel tous les dossiers de sortie intermédiaires spécifiques à la configuration sont créés. La valeur par défaut est `obj\`. Le code suivant est un exemple : `<BaseIntermediateOutputPath>c:\xyz\obj\</BaseIntermediateOutputPath>` |
| BuildInParallel | Valeur booléenne qui indique si les références de projet sont générées ou nettoyées en parallèle lorsque [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] est utilisé en multiprocesseur. La valeur par défaut est `true`, ce qui signifie que les projets seront générés en parallèle si le système possède plusieurs cœurs ou processeurs. |
| BuildProjectReferences | Valeur booléenne qui indique si les références de projet sont générées par [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Affectez automatiquement la valeur `false` si vous générez votre projet dans l’environnement de développement intégré (IDE) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ou `true` dans le cas contraire. `-p:BuildProjectReferences=false` peut être spécifié sur la ligne de commande pour éviter de vérifier si les projets référencés sont à jour. |
| CleanFile | Nom du fichier qui sera utilisé comme « nettoyeur de cache ». Ce fichier contient une liste de fichiers générés à supprimer pendant l'opération de nettoyage. Le fichier est placé dans le chemin de sortie intermédiaire par le processus de génération.<br /><br /> Cette propriété spécifie uniquement des noms de fichier qui n'ont pas d'informations de chemin d'accès. |
| CodePage | Spécifie la page de codes à utiliser pour tous les fichiers de code source inclus dans la compilation. Cette propriété est équivalente au commutateur `/codepage` du compilateur. |
| CompilerResponseFile | Fichier réponse facultatif qui peut être passé aux tâches du compilateur. |
| Configuration | Configuration que vous générez, "Debug" ou "Release". |
| CscToolPath | Chemin de *csc.exe*, le compilateur [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]. |
| CustomBeforeMicrosoftCommonTargets | Nom d'un fichier projet ou fichier de cibles qui doit être importé automatiquement avant l'importation des cibles communes. |
| DebugSymbols | Valeur booléenne qui indique si les symboles sont générés par la procédure.<br /><br /> En spécifiant **/p:DebugSymbols=false** en ligne de commande, vous désactivez la génération de fichiers de symboles de la base de données du programme (*.pdb*). |
| DebugType | Définit le niveau d'informations de débogage que vous souhaitez générer. Les valeurs valides sont « full », « pdbonly », « portable », « embedded » et « none ». |
| DefineConstants | Définit des constantes conditionnelles du compilateur. Les paires symbole/valeur sont séparées par des points-virgules et spécifiées avec la syntaxe suivante :<br /><br /> *symbole1 = valeur1 ; symbole2 = valeur2*<br /><br /> Cette propriété est équivalente au commutateur `/define` du compilateur. |
| DefineDebug | Valeur booléenne qui indique si vous souhaitez que la constante DEBUG soit définie. |
| DefineTrace | Valeur booléenne qui indique si vous souhaitez que la constante TRACE soit définie. |
| DelaySign | Valeur booléenne qui indique si vous souhaitez différer la signature de l'assembly plutôt que le signer complètement. |
| Déterministe | Valeur booléenne qui indique si le compilateur doit produire des assemblys identiques pour des entrées identiques. Ce paramètre correspond au commutateur `/deterministic` des compilateurs *vbc.exe* et *csc.exe*. |
| DisabledWarnings | Supprime les avertissements spécifiés. Seule la partie numérique de l'identificateur d'avertissement doit être spécifiée. Les différents avertissements sont séparés par des points-virgules. Ce paramètre correspond au commutateur `/nowarn` du compilateur *vbc.exe*. |
| DisableFastUpToDateCheck | Valeur booléenne qui s'applique uniquement à [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Le gestionnaire de génération [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] utilise un processus appelé FastUpToDateCheck pour déterminer si un projet doit être régénéré pour être à jour. Il est plus rapide d'utiliser ce processus que [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Le fait d’affecter à la propriété DisableFastUpToDateCheck la valeur `true` vous permet d’ignorer le gestionnaire de build [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et de le forcer à utiliser [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] pour déterminer si le projet est à jour. |
| DocumentationFile | Nom du fichier généré en tant que fichier de documentation XML. Ce nom inclut uniquement le nom du fichier et ne comporte aucune information de chemin d'accès. |
| ErrorReport | Indique comment la tâche du compilateur doit signaler les erreurs internes du compilateur. Les valeurs valides sont "prompt", "send" et "none". Cette propriété est équivalente au commutateur `/errorreport` du compilateur. |
| ExcludeDeploymentUrl | La [tâche GenerateDeploymentManifest](../msbuild/generatedeploymentmanifest-task.md) ajoute une balise deploymentProvider au manifeste de déploiement si le fichier projet contient l’un des éléments suivants :<br /><br /> -   UpdateUrl<br />-   InstallUrl<br />-   PublishUrl<br /><br /> En utilisant ExcludeDeploymentUrl, toutefois, vous pouvez empêcher l’étiquette deploymentProvider d’être ajoutée au manifeste de déploiement même si l’une des URL ci-dessus est spécifiée. Pour cela, ajoutez la propriété suivante à votre fichier projet :<br /><br /> `<ExcludeDeploymentUrl>true</ExcludeDeploymentUrl>` <br /><br />**Remarque :**  ExcludeDeploymentUrl n'est pas exposé dans l'IDE de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et peut être défini uniquement en modifiant manuellement le fichier projet. La définition de cette propriété n'affecte pas la publication dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Autrement dit, la balise deploymentProvider est encore ajoutée à l'URL spécifiée par PublishUrl. |
| FileAlignment | Spécifie, en octets, où les sections du fichier de sortie doivent être alignées. Les valeurs valides sont 512, 1024, 2048, 4096, 8192. Cette propriété est équivalente au commutateur `/filealignment` du compilateur. |
| FrameworkPathOverride | Spécifie l’emplacement de *mscorlib.dll* et de *microsoft.visualbasic.dll*. Ce paramètre est équivalent au commutateur `/sdkpath` du compilateur *vbc.exe*. |
| GenerateDocumentation | (Visual Basic uniquement) Paramètre booléen qui indique si la documentation est générée par la build. Si sa valeur est `true`, les informations de documentation sont générées et placées dans un fichier *.xml* avec le nom de la bibliothèque ou du fichier exécutable créé par la tâche de génération. |
| GenerateSerializationAssemblies | Indique si les assemblys de sérialisation XML doivent être générés par *SGen.exe*, qui peut être défini sur on, auto ou off. Cette propriété est utilisée pour les assemblys qui ciblent le .NET Framework uniquement. Pour générer des assemblys de sérialisation XML pour des assemblys .NET Standard ou .NET Core, référencez le package NuGet *Microsoft.XmlSerializer.Generator*. |
| IntermediateOutputPath | Chemin de sortie intermédiaire complet dérivé de `BaseIntermediateOutputPath`, si aucun chemin d'accès n'est spécifié. Par exemple, *\obj\debug\\*. |
| KeyContainerName | Nom du conteneur de clé de nom fort. |
| KeyOriginatorFile | Nom du fichier de clé de nom fort. |
| MSBuildProjectExtensionsPath | Spécifie le chemin dans lequel se trouvent les extensions de projet. Sa valeur par défaut est la même que `BaseIntermediateOutputPath`. |
| ModuleAssemblyName | Nom de l'assembly dans lequel le module compilé doit être incorporé. Cette propriété est équivalente au commutateur `/moduleassemblyname` du compilateur. |
| NoLogo | Valeur booléenne qui indique si vous souhaitez que le logo du compilateur soit désactivé. Cette propriété est équivalente au commutateur `/nologo` du compilateur. |
| NoStdLib | Valeur booléenne qui indique s’il faut éviter de référencer la bibliothèque standard (*mscorlib.dll*). La valeur par défaut est `false`. |
| NoVBRuntimeReference | Valeur booléenne qui indique si le runtime [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] (*Microsoft.VisualBasic.dll*) doit être inclus comme référence dans le projet. |
| NoWin32Manifest | Valeur booléenne qui indique si les informations de manifeste de Contrôle de compte d'utilisateur seront incorporées dans l'exécutable de l'application. S'applique uniquement aux projets Visual Studio ciblant [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)]. Dans les projets déployés à l'aide de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] et de COM sans inscription, cet élément est ignoré. `False` (valeur par défaut) spécifie que les informations de manifeste de Contrôle de compte d'utilisateur doivent être incorporées dans le fichier exécutable de l'application. `True` spécifie que les informations de manifeste de Contrôle de compte d'utilisateur ne doivent pas être incorporées.<br /><br /> Cette propriété s'applique uniquement aux projets [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ciblant [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)]. Dans les projets déployés à l'aide de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] et de COM sans inscription, cette propriété est ignorée.<br /><br /> Vous ne devez ajouter NoWin32Manifest que si vous ne voulez pas que [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] incorpore la moindre information de manifeste dans l’exécutable de l’application ; ce processus s’appelle *virtualisation*. Pour utiliser la virtualisation, définissez `<ApplicationManifest>` conjointement à `<NoWin32Manifest>`, comme suit :<br /><br /> -   Pour les projets [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], supprimez le nœud `<ApplicationManifest>`. (Dans les projets [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], `<NoWin32Manifest>` est ignoré s’il existe un nœud `<ApplicationManifest>`.)<br />-   Pour les projets [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], affectez à `<ApplicationManifest>` la valeur `False` et à `<NoWin32Manifest>` la valeur `True`. (Dans les projets [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], `<ApplicationManifest>` remplace `<NoWin32Manifest>`.)<br /> Cette propriété est équivalente au commutateur `/nowin32manifest` du compilateur *vbc.exe*. |
| Optimize | Valeur booléenne qui, lorsqu'elle correspond à `true`, active les optimisations du compilateur. Cette propriété est équivalente au commutateur `/optimize` du compilateur. |
| OptionCompare | Spécifie la façon dont sont effectuées les comparaisons de chaînes. Les valeurs valides sont "binary" et "text". Cette propriété est équivalente au commutateur `/optioncompare` du compilateur *vbc.exe*. |
| OptionExplicit | Valeur booléenne qui, lorsqu'elle correspond à `true`, requiert une déclaration explicite des variables dans le code source. Cette propriété est équivalente au commutateur `/optionexplicit` du compilateur. |
| OptionInfer | Valeur booléenne qui, lorsqu'elle correspond à `true`, active l'inférence de type des variables. Cette propriété est équivalente au commutateur `/optioninfer` du compilateur. |
| OptionStrict | Valeur booléenne qui, lorsqu'elle correspond à `true`, pousse la tâche de génération à appliquer une sémantique de type stricte pour restreindre les conversions de types implicites. Cette propriété est équivalente au commutateur `/optionstrict` du compilateur *vbc.exe*. |
| OutputPath | Spécifie le chemin du répertoire de sortie, relatif au répertoire de projet, par exemple *bin\Debug*. |
| OutputType | Spécifie le format de fichier du fichier de sortie. Ce paramètre peut prendre l'une des valeurs suivantes :<br /><br /> -   Library. Crée une bibliothèque de code. (Valeur par défaut)<br />-   Exe. Crée une application console.<br />-   Module. Crée un module.<br />-   Winexe. Crée un programme Windows.<br /><br /> Cette propriété est équivalente au commutateur `/target` du compilateur *vbc.exe*. |
| OverwriteReadOnlyFiles | Valeur booléenne qui indique si vous souhaitez permettre à la génération de remplacer les fichiers en lecture seule ou de générer une erreur. |
| PathMap | Valeur qui indique comment mapper les chemins d’accès physiques avec les noms de chemins d’accès sources générés en sortie par le compilateur. Cette propriété est équivalente au commutateur `/pathmap` du compilateur *csc.exe*. |
| PdbFile | Nom du fichier *.pdb* que vous émettez. Cette propriété est équivalente au commutateur `/pdb` du compilateur *csc.exe*. |
| Plateforme | Système d'exploitation pour lequel vous générez la cible. Les valeurs valides sont « Any CPU », « x86 » et « x64 ». |
| ProduceReferenceAssembly | Valeur booléenne qui, lorsqu’elle est définie sur `true`, permet la production d’[assemblys de référence](https://github.com/dotnet/roslyn/blob/master/docs/features/refout.md) pour l’assembly actuel. `Deterministic` doit être `true` lors de l’utilisation de cette fonctionnalité. Cette propriété correspond au commutateur `/refout` des compilateurs *vbc.exe* et *csc.exe*. |
| ProduceOnlyReferenceAssembly | Valeur booléenne qui spécifie que le compilateur doit seulement émettre un assembly de référence, plutôt que le code compilé. Non utilisable avec `ProduceReferenceAssembly`.  Cette propriété correspond au commutateur `/refonly` des compilateurs *vbc.exe* et *csc.exe*. |
| RemoveIntegerChecks | Valeur booléenne indiquant s'il convient de désactiver les contrôles d'erreurs de dépassement sur les entiers. La valeur par défaut est `false`. Cette propriété est équivalente au commutateur `/removeintchecks` du compilateur *vbc.exe*. |
| SGenUseProxyTypes | Valeur booléenne qui indique si les types de proxy doivent être générés par *SGen.exe*. Cela vaut uniquement quand *GenerateSerializationAssemblies* est défini sur on et pour le .NET Framework uniquement.<br /><br /> La cible SGen utilise cette propriété pour définir l'indicateur UseProxyTypes. Cette propriété a true comme valeur par défaut et aucune option d'interface utilisateur ne permet de modifier cela. Pour générer l’assembly de sérialisation pour les types non-webservice, ajoutez cette propriété au fichier projet et affectez-lui la valeur false avant d’importer *Microsoft.Common.Targets* ou *C#/VB.targets*. |
| SGenToolPath | Chemin de l’outil facultatif qui indique où obtenir *SGen.exe* quand la version actuelle de *SGen.exe* est remplacée. Cette propriété est utilisée pour le .NET Framework uniquement.|
| StartupObject | Spécifie la classe ou le module qui contient la méthode Main ou la procédure Sub Main. Cette propriété est équivalente au commutateur `/main` du compilateur. |
| ProcessorArchitecture | Architecture de processeur utilisée lorsque les références d'assembly sont résolues. Les valeurs valides sont "msil", "x86", "amd64" et "ia64". |
| RootNamespace | Espace de noms racine à utiliser lorsque vous nommez une ressource incorporée. Cet espace de noms fait partie du nom du manifeste de ressources incorporées. |
| Satellite_AlgorithmId | ID de l’algorithme de hachage *AL.exe* à utiliser quand les assemblys satellites sont créés. |
| Satellite_BaseAddress | Adresse de base à utiliser lorsque les assemblys satellites spécifiques à la culture sont générés en utilisant la cible `CreateSatelliteAssemblies`. |
| Satellite_CompanyName | Nom de la société à passer à *AL.exe* pendant la génération d’assembly satellite. |
| Satellite_Configuration | Nom de configuration à passer à *AL.exe* pendant la génération d’assembly satellite. |
| Satellite_Description | Texte descriptif à passer à *AL.exe* pendant la génération d’assembly satellite. |
| Satellite_EvidenceFile | Incorpore le fichier spécifié dans l'assembly satellite qui possède le nom de ressource "Security.Evidence". |
| Satellite_FileVersion | Spécifie une chaîne pour le champ Version de fichier de l'assembly satellite. |
| Satellite_Flags | Spécifie une valeur pour le champ Indicateurs de l'assembly satellite. |
| Satellite_GenerateFullPaths | Force la tâche de génération à utiliser des chemins d'accès absolus pour tous les fichiers signalés dans un message d'erreur. |
| Satellite_LinkResource | Lie les fichiers de ressources spécifiés à un assembly satellite. |
| Satellite_MainEntryPoint | Spécifie le nom qualifié complet (autrement dit, class.method) de la méthode à utiliser comme point d'entrée lorsqu'un module est converti en fichier exécutable pendant la génération d'assembly satellite. |
| Satellite_ProductName | Spécifie une chaîne pour le champ Produit de l'assembly satellite. |
| Satellite_ProductVersion | Spécifie une chaîne pour le champ ProductVersion de l'assembly satellite. |
| Satellite_TargetType | Spécifie le format de fichier du fichier de sortie de l'assembly satellite : "library", "exe" ou "win". La valeur par défaut est "library". |
| Satellite_Title | Spécifie une chaîne pour le champ Titre de l'assembly satellite. |
| Satellite_Trademark | Spécifie une chaîne pour le champ Marque déposée de l'assembly satellite. |
| Satellite_Version | Spécifie les informations de version concernant l'assembly satellite. |
| Satellite_Win32Icon | Insère un fichier icône *.ico* dans l’assembly satellite. |
| Satellite_Win32Resource | Insère une ressource Win32 (fichier *.res*) dans l’assembly satellite. |
| SubsystemVersion | Spécifie la version minimale du sous-système utilisable par le fichier exécutable généré. Cette propriété est équivalente au commutateur `/subsystemversion` du compilateur. Pour plus d’informations sur la valeur par défaut de cette propriété, consultez [/subsystemversion (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/subsystemversion) ou [/subsystemversion (options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/subsystemversion-compiler-option). |
| TargetCompactFramework | Version du .NET Compact Framework requise pour exécuter l'application que vous générez. La spécification de ce paramètre vous permet de référencer certains assemblys Framework que vous ne pourriez peut-être pas référencer autrement. |
| TargetFrameworkVersion | Version du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] nécessaire pour exécuter l’application que vous générez. La spécification de ce paramètre vous permet de référencer certains assemblys Framework que vous ne pourriez peut-être pas référencer autrement. |
| TreatWarningsAsErrors | Paramètre booléen qui, s'il a pour valeur `true`, entraîne le traitement de tous les avertissements comme des erreurs. Ce paramètre est équivalent au commutateur `/nowarn` du compilateur. |
| UseHostCompilerIfAvailable | Paramètre booléen qui, s'il a pour valeur `true`, force la tâche de génération à utiliser l'objet de compilateur in-process, s'il est disponible. Ce paramètre est utilisé uniquement par [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. |
| Utf8Output | Paramètre booléen qui, s'il a pour valeur `true`, consigne la sortie du compilateur en utilisant l'encodage UTF-8. Ce paramètre est équivalent au commutateur `/utf8Output` du compilateur. |
| VbcToolPath | Chemin facultatif qui indique un autre emplacement pour *vbc.exe* quand la version actuelle de *vbc.exe* est remplacée. |
| VbcVerbosity | Spécifie le niveau de détail de la sortie du compilateur [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. Les valeurs valides sont « Quiet », « Normal » (valeur par défaut) et « Verbose ». |
| VisualStudioVersion | Spécifie la version de Visual Studio dans laquelle ce projet doit être considéré comme s'exécutant. Si cette propriété est omise, MSBuild la définit en tant que valeur par défaut raisonnable.<br /><br /> Cette propriété est utilisée dans plusieurs types de projet pour spécifier l'ensemble des cibles utilisées pour la génération. Si `ToolsVersion` a la valeur 4.0 ou ultérieure pour un projet, `VisualStudioVersion` est utilisé pour spécifier le sous-ensemble d'outils à utiliser. Pour plus d’informations, consultez [Ensemble d’outils (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md). |
| WarningsAsErrors | Spécifie une liste d'avertissements à traiter comme des erreurs. Ce paramètre est équivalent au commutateur `/warnaserror` du compilateur. |
| WarningsNotAsErrors | Spécifie une liste d'avertissements à ne pas traiter comme des erreurs. Ce paramètre est équivalent au commutateur `/warnaserror` du compilateur. |
| Win32Manifest | Nom du fichier manifeste qui doit être incorporé dans l'assembly final. Ce paramètre est équivalent au commutateur `/win32Manifest` du compilateur. |
| Win32Resource | Nom de fichier de la ressource Win32 à incorporer dans l'assembly final. Ce paramètre est équivalent au commutateur `/win32resource` du compilateur. |

## <a name="see-also"></a>Voir aussi
- [Éléments communs des projets MSBuild](../msbuild/common-msbuild-project-items.md)
