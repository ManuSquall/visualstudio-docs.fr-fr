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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 238b963aceebd2bfdae38c2f4032955c1bd0c0c6
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85288947"
---
# <a name="common-msbuild-project-properties"></a>Propriétés communes des projets MSBuild

Le tableau suivant répertorie les propriétés fréquemment utilisées qui sont définies dans les fichiers projet Visual Studio ou incluses dans les fichiers *. targets* fournis par MSBuild.

 Les fichiers projet dans Visual Studio (*.csproj*, *.vbproj*, *.vcxproj* et autres) contiennent le code XML MSBuild qui s’exécute quand vous générez un projet à l’aide de l’IDE. Les projets importent généralement un ou plusieurs fichiers *. targets* pour définir leur processus de génération. Pour plus d’informations, consultez [Fichiers .targets MSBuild](../msbuild/msbuild-dot-targets-files.md).

## <a name="list-of-common-properties-and-parameters"></a>Liste des propriétés et paramètres courants

| Nom de propriété ou de paramètre | Types de projet | Description |
|------------------------------------| - | - |
| AdditionalLibPaths | .NET | Spécifie des dossiers supplémentaires dans lesquels les compilateurs doivent rechercher des assemblys de référence. |
| AddModules | .NET | Entraîne la mise à disposition par le compilateur de toutes les informations de type à partir des fichiers spécifiés, pour le projet en cours de compilation. Cette propriété est équivalente au commutateur `/addModules` du compilateur. |
| ALToolPath | .NET | Chemin d’accès où se trouve *AL.exe* . Cette propriété remplace la version actuelle de *AL.exe* pour permettre l’utilisation d’une version différente. |
| ApplicationIcon | .NET | Fichier icône *. ico* à passer au compilateur pour qu’il soit incorporé en tant qu’icône Win32. Cette propriété est équivalente au commutateur `/win32icon` du compilateur. |
| ApplicationManifest | Tous | Spécifie le chemin d'accès du fichier utilisé pour générer les informations de manifeste de Contrôle de compte d'utilisateur externe. S’applique uniquement aux projets Visual Studio ciblant Windows Vista.<br /><br /> Dans la plupart des cas, le manifeste est incorporé. Toutefois, si vous utilisez un déploiement COM ou ClickOnce gratuit, le manifeste peut être un fichier externe installé avec vos assemblys d’application. Pour plus d'informations, consultez la propriété NoWin32Manifest dans cette rubrique. |
| AssemblyOriginatorKeyFile | .NET | Spécifie le fichier utilisé pour signer l’assembly (*.snk* ou *.pfx*) et passé à la [tâche ResolveKeySource](../msbuild/resolvekeysource-task.md) pour générer la clé réelle utilisée pour signer l’assembly. |
| AssemblySearchPaths | .NET | Liste d'emplacements dans lesquels il convient de rechercher au cours de la résolution de l'assembly de référence au moment de la génération. L'ordre dans lequel les chemins d'accès apparaissent dans cette liste est significatif, car les chemins répertoriés antérieurement ont priorité sur les entrées ultérieures. |
| AssemblyName | .NET | Nom de l'assembly de sortie définitif après génération du projet. |
| BaseAddress | .NET | Spécifie l'adresse de base de l'assembly de sortie principal. Cette propriété est équivalente au commutateur `/baseaddress` du compilateur. |
| BaseIntermediateOutputPath | Tous | Dossier de niveau supérieur dans lequel tous les dossiers de sortie intermédiaires spécifiques à la configuration sont créés. La valeur par défaut est `obj\`. Le code suivant est un exemple : `<BaseIntermediateOutputPath>c:\xyz\obj\</BaseIntermediateOutputPath>` |
| BaseOutputPath | Tous | Spécifie le chemin d'accès de base du fichier de sortie. S’il est défini, MSBuild utilise `OutputPath = $(BaseOutputPath)\$(Configuration)\` . Exemple de syntaxe : `<BaseOutputPath>c:\xyz\bin\</BaseOutputPath>` |
| BuildInParallel | Tous | Valeur booléenne qui indique si les références de projet sont générées ou nettoyées en parallèle quand MSBuild multi-proc est utilisé. La valeur par défaut est `true`, ce qui signifie que les projets seront générés en parallèle si le système possède plusieurs cœurs ou processeurs. |
| BuildProjectReferences | Tous | Valeur booléenne qui indique si les références de projet sont générées par MSBuild. Défini automatiquement sur `false` si vous générez votre projet dans l’environnement de développement intégré (IDE) de Visual Studio, dans le cas `true` contraire. `-p:BuildProjectReferences=false` peut être spécifié sur la ligne de commande pour éviter de vérifier si les projets référencés sont à jour. |
| CleanFile | Tous | Nom du fichier qui sera utilisé comme « nettoyeur de cache ». Ce fichier contient une liste de fichiers générés à supprimer pendant l'opération de nettoyage. Le fichier est placé dans le chemin de sortie intermédiaire par le processus de génération.<br /><br /> Cette propriété spécifie uniquement des noms de fichier qui n'ont pas d'informations de chemin d'accès. |
| CodePage | .NET | Spécifie la page de codes à utiliser pour tous les fichiers de code source inclus dans la compilation. Cette propriété est équivalente au commutateur `/codepage` du compilateur. |
| CompilerResponseFile | .NET | Fichier réponse facultatif qui peut être passé aux tâches du compilateur. |
| Configuration | Tous | Configuration que vous générez, "Debug" ou "Release". |
| CscToolPath | C# | Le chemin d’accès de *csc.exe*, le compilateur C#. |
| CustomBeforeMicrosoftCommonTargets | Tous | Nom d'un fichier projet ou fichier de cibles qui doit être importé automatiquement avant l'importation des cibles communes. |
| DebugSymbols | Tous | Valeur booléenne qui indique si les symboles sont générés par la procédure.<br /><br /> La définition de **-p :DebugSymbols = false** sur la ligne de commande désactive la génération de fichiers de symboles de base de données du programme (*. pdb*). |
| DebugType | Tous | Définit le niveau d'informations de débogage que vous souhaitez générer. Les valeurs valides sont « full », « pdbonly », « portable », « embedded » et « none ». |
| DefineConstants | .NET | Définit des constantes conditionnelles du compilateur. Les paires symbole/valeur sont séparées par des points-virgules et spécifiées avec la syntaxe suivante :<br /><br /> *symbole1 = valeur1 ; symbole2 = valeur2*<br /><br /> Cette propriété est équivalente au commutateur `/define` du compilateur. |
| DefineDebug | Tous |  Valeur booléenne qui indique si vous souhaitez que la constante DEBUG soit définie. |
| DefineTrace | Tous | Valeur booléenne qui indique si vous souhaitez que la constante TRACE soit définie. |
| DelaySign | .NET | Valeur booléenne qui indique si vous souhaitez différer la signature de l'assembly plutôt que le signer complètement. |
| Déterministe | .NET | Valeur booléenne qui indique si le compilateur doit produire des assemblys identiques pour des entrées identiques. Ce paramètre correspond au `/deterministic` commutateur des compilateurs. |
| DisableFastUpToDateCheck | Tous | Valeur booléenne qui s’applique uniquement à Visual Studio. Le gestionnaire de build de Visual Studio utilise un processus appelé FastUpToDateCheck pour déterminer si un projet doit être régénéré pour être à jour. Ce processus est plus rapide que l’utilisation de MSBuild pour déterminer cela. L’affectation de la valeur à la propriété DisableFastUpToDateCheck `true` vous permet de contourner le gestionnaire de build de Visual Studio et de l’obliger à utiliser MSBuild pour déterminer si le projet est à jour. |
| DocumentationFile | .NET | Nom du fichier généré en tant que fichier de documentation XML. Ce nom inclut uniquement le nom du fichier et ne comporte aucune information de chemin d'accès. |
| ErrorReport | .NET | Indique comment la tâche du compilateur doit signaler les erreurs internes du compilateur. Les valeurs valides sont "prompt", "send" et "none". Cette propriété est équivalente au commutateur `/errorreport` du compilateur. |
| ExcludeDeploymentUrl | .NET | La [tâche GenerateDeploymentManifest](../msbuild/generatedeploymentmanifest-task.md) ajoute une balise deploymentProvider au manifeste de déploiement si le fichier projet inclut l’un des éléments suivants :<br /><br /> -   UpdateUrl<br />-   InstallUrl<br />-   PublishUrl<br /><br /> En utilisant ExcludeDeploymentUrl, toutefois, vous pouvez empêcher l’étiquette deploymentProvider d’être ajoutée au manifeste de déploiement même si l’une des URL ci-dessus est spécifiée. Pour cela, ajoutez la propriété suivante à votre fichier projet :<br /><br /> `<ExcludeDeploymentUrl>true</ExcludeDeploymentUrl>` <br /><br />**Remarque :**  ExcludeDeploymentUrl n’est pas exposé dans l’IDE de Visual Studio et ne peut être défini qu’en modifiant manuellement le fichier projet. La définition de cette propriété n’affecte pas la publication dans Visual Studio. autrement dit, la balise deploymentProvider sera toujours ajoutée à l’URL spécifiée par PublishUrl. |
| FileAlignment | .NET | Spécifie, en octets, où les sections du fichier de sortie doivent être alignées. Les valeurs valides sont 512, 1024, 2048, 4096, 8192. Cette propriété est équivalente au commutateur `/filealignment` du compilateur. |
| FrameworkPathOverride | Visual Basic | Spécifie l’emplacement des *mscorlib.dll* et des *microsoft.visualbasic.dll*. Ce paramètre est équivalent au `/sdkpath` commutateur du compilateur *vbc.exe* . |
| GenerateDocumentation | .NET | Paramètre booléen qui indique si la documentation est générée par la procédure. Si `true` , la génération génère des informations de documentation et les place dans un fichier *. xml* avec le nom de la bibliothèque ou du fichier exécutable créé par la tâche de génération. |
| GenerateFullPaths | C# | Générez des chemins d’accès complets pour les noms de fichiers dans la sortie à l’aide de l’option [de compilateur-fullpaths](/dotnet/csharp/language-reference/compiler-options/fullpaths-compiler-option) . |
| GenerateSerializationAssemblies | .NET | Indique si les assemblys de sérialisation XML doivent être générés par *SGen.exe*, qui peut être défini sur on, auto ou off. Cette propriété est utilisée pour les assemblys qui ciblent le .NET Framework uniquement. Pour générer des assemblys de sérialisation XML pour des assemblys .NET Standard ou .NET Core, référencez le package NuGet *Microsoft.XmlSerializer.Generator*. |
| IntermediateOutputPath | Tous | Chemin de sortie intermédiaire complet dérivé de `BaseIntermediateOutputPath`, si aucun chemin d'accès n'est spécifié. Par exemple, *\obj\debug \\ *. |
| KeyContainerName | Tous | Nom du conteneur de clé de nom fort. |
| KeyOriginatorFile | Tous | Nom du fichier de clé de nom fort. |
| ModuleAssemblyName | .NET | Nom de l'assembly dans lequel le module compilé doit être incorporé. Cette propriété est équivalente au commutateur `/moduleassemblyname` du compilateur. |
| MSBuildProjectExtensionsPath | Tous | Spécifie le chemin dans lequel se trouvent les extensions de projet. Sa valeur par défaut est la même que `BaseIntermediateOutputPath`. |
| NoLogo | Tous | Valeur booléenne qui indique si vous souhaitez que le logo du compilateur soit désactivé. Cette propriété est équivalente au commutateur `/nologo` du compilateur. |
| NoStdLib | .NET | Valeur booléenne qui indique s’il faut éviter de référencer la bibliothèque standard (*mscorlib.dll*). La valeur par défaut est `false`. |
| NoVBRuntimeReference | Visual Basic | Valeur booléenne qui indique si le Visual Basic Runtime (*Microsoft.VisualBasic.dll*) doit être inclus comme référence dans le projet. |
| NoWarn | .NET | Supprime les avertissements spécifiés. Seule la partie numérique de l'identificateur d'avertissement doit être spécifiée. Les différents avertissements sont séparés par des points-virgules. Ce paramètre correspond au `/nowarn` commutateur des compilateurs. |
| NoWin32Manifest | .NET | Valeur booléenne qui indique si les informations de manifeste de Contrôle de compte d'utilisateur seront incorporées dans l'exécutable de l'application. S’applique uniquement aux projets Visual Studio ciblant Windows Vista. Dans les projets déployés à l’aide de ClickOnce et de COM sans inscription, cet élément est ignoré. `False` (valeur par défaut) spécifie que les informations de manifeste de Contrôle de compte d'utilisateur doivent être incorporées dans le fichier exécutable de l'application. `True` spécifie que les informations de manifeste de Contrôle de compte d'utilisateur ne doivent pas être incorporées.<br /><br /> Cette propriété s’applique uniquement aux projets Visual Studio ciblant Windows Vista. Dans les projets déployés à l’aide de ClickOnce et de COM sans inscription, cette propriété est ignorée.<br /><br /> Vous ne devez ajouter NoWin32Manifest que si vous ne souhaitez pas que Visual Studio incorpore des informations de manifeste dans l’exécutable de l’application. Ce processus est appelé *virtualisation*. Pour utiliser la virtualisation, définissez `<ApplicationManifest>` conjointement à `<NoWin32Manifest>`, comme suit :<br /><br /> -Pour les projets Visual Basic, supprimez le `<ApplicationManifest>` nœud. (Dans Visual Basic projets, `<NoWin32Manifest>` est ignoré lorsqu’un `<ApplicationManifest>` nœud existe.)<br />-Pour les projets C#, affectez à la valeur `<ApplicationManifest>` `False` et `<NoWin32Manifest>` à `True` . (Dans les projets C#, `<ApplicationManifest>` remplace `<NoWin32Manifest>` .)<br /> Cette propriété est équivalente au `/nowin32manifest` commutateur du compilateur de *vbc.exe*. |
| Optimiser | .NET | Valeur booléenne qui, lorsqu'elle correspond à `true`, active les optimisations du compilateur. Cette propriété est équivalente au commutateur `/optimize` du compilateur. |
| OptionCompare | VisualBasic | Spécifie la façon dont sont effectuées les comparaisons de chaînes. Les valeurs valides sont "binary" et "text". Cette propriété est équivalente au `/optioncompare` commutateur du compilateur de *vbc.exe*. |
| OptionExplicit | Visual Basic | Valeur booléenne qui, lorsqu'elle correspond à `true`, requiert une déclaration explicite des variables dans le code source. Cette propriété est équivalente au commutateur `/optionexplicit` du compilateur. |
| OptionInfer | Visual Basic | Valeur booléenne qui, lorsqu'elle correspond à `true`, active l'inférence de type des variables. Cette propriété est équivalente au commutateur `/optioninfer` du compilateur. |
| OptionStrict | Visual Basic | Valeur booléenne qui, lorsqu'elle correspond à `true`, pousse la tâche de génération à appliquer une sémantique de type stricte pour restreindre les conversions de types implicites. Cette propriété est équivalente au `/optionstrict` commutateur du compilateur *vbc.exe* . |
| OutDir | Tous | Indique l’emplacement de sortie final pour le projet ou la solution. Lors de la génération d’une solution, OutDir peut être utilisé pour regrouper plusieurs sorties de projet à un seul emplacement. En outre, OutDir est inclus dans AssemblySearchPaths utilisé pour la résolution des références. Par exemple, *bin\Debug*. |
| OutputPath | Tous | Spécifie le chemin du répertoire de sortie, relatif au répertoire de projet, par exemple *bin\Debug*. |
| OutputType | Tous |  Spécifie le format de fichier du fichier de sortie. Ce paramètre peut prendre l'une des valeurs suivantes :<br /><br /> -   Library. Crée une bibliothèque de code. (Valeur par défaut)<br />-   Exe. Crée une application console.<br />-   Module. Crée un module.<br />-   Winexe. Crée un programme Windows.<br /><br /> Pour C# et Visual Basic, cette propriété est équivalente au `/target` commutateur. |
| OverwriteReadOnlyFiles | Tous | Valeur booléenne qui indique si vous souhaitez permettre à la génération de remplacer les fichiers en lecture seule ou de générer une erreur. |
| PathMap | .NET | Valeur qui indique comment mapper les chemins d’accès physiques avec les noms de chemins d’accès sources générés en sortie par le compilateur. Cette propriété est équivalente au `/pathmap` commutateur des compilateurs. |
| PdbFile | .NET | Nom du fichier *.pdb* que vous émettez. Cette propriété est équivalente au commutateur `/pdb` du compilateur *csc.exe*. |
| Plateforme | Tous | Système d'exploitation pour lequel vous générez la cible. Les exemples pour les builds de .NET Framework sont « Any CPU », « x86 » et « x64 ». |
| ProcessorArchitecture | .NET | Architecture de processeur utilisée lorsque les références d'assembly sont résolues. Les valeurs valides sont "msil", "x86", "amd64" et "ia64". |
| ProduceOnlyReferenceAssembly | .NET | Valeur booléenne qui spécifie que le compilateur doit seulement émettre un assembly de référence, plutôt que le code compilé. Non utilisable avec `ProduceReferenceAssembly`.  Cette propriété correspond au commutateur `/refonly` des compilateurs *vbc.exe* et *csc.exe*. |
| ProduceReferenceAssembly | .NET | Valeur booléenne qui, lorsqu’elle est définie sur `true`, permet la production d’[assemblys de référence](/dotnet/standard/assembly/reference-assemblies) pour l’assembly actuel. `Deterministic` doit être `true` lors de l’utilisation de cette fonctionnalité. Cette propriété correspond au commutateur `/refout` des compilateurs *vbc.exe* et *csc.exe*. |
| RemoveIntegerChecks | Visual Basic | Valeur booléenne indiquant s'il convient de désactiver les contrôles d'erreurs de dépassement sur les entiers. La valeur par défaut est `false`. Cette propriété est équivalente au `/removeintchecks` commutateur du compilateur *vbc.exe* . |
| RootNamespace | Tous | Espace de noms racine à utiliser lorsque vous nommez une ressource incorporée. Cet espace de noms fait partie du nom du manifeste de ressources incorporées. |
| Satellite_AlgorithmId | .NET | ID de l’algorithme de hachage *AL.exe* à utiliser quand les assemblys satellites sont créés. |
| Satellite_BaseAddress | .NET | Adresse de base à utiliser lorsque les assemblys satellites spécifiques à la culture sont générés en utilisant la cible `CreateSatelliteAssemblies`. |
| Satellite_CompanyName | .NET | Nom de la société à passer à *AL.exe* pendant la génération d’assembly satellite. |
| Satellite_Configuration | .NET | Nom de configuration à passer à *AL.exe* pendant la génération d’assembly satellite. |
| Satellite_Description | .NET | Texte descriptif à passer à *AL.exe* pendant la génération d’assembly satellite. |
| Satellite_EvidenceFile | .NET | Incorpore le fichier spécifié dans l'assembly satellite qui possède le nom de ressource "Security.Evidence". |
| Satellite_FileVersion | .NET | Spécifie une chaîne pour le champ Version de fichier de l'assembly satellite. |
| Satellite_Flags | .NET | Spécifie une valeur pour le champ Indicateurs de l'assembly satellite. |
| Satellite_GenerateFullPaths | .NET | Force la tâche de génération à utiliser des chemins d'accès absolus pour tous les fichiers signalés dans un message d'erreur. |
| Satellite_LinkResource | .NET | Lie les fichiers de ressources spécifiés à un assembly satellite. |
| Satellite_MainEntryPoint | .NET | Spécifie le nom qualifié complet (autrement dit, class.method) de la méthode à utiliser comme point d'entrée lorsqu'un module est converti en fichier exécutable pendant la génération d'assembly satellite. |
| Satellite_ProductName | .NET | Spécifie une chaîne pour le champ Produit de l'assembly satellite. |
| Satellite_ProductVersion | .NET | Spécifie une chaîne pour le champ ProductVersion de l'assembly satellite. |
| Satellite_TargetType | .NET | Spécifie le format de fichier du fichier de sortie de l'assembly satellite : "library", "exe" ou "win". La valeur par défaut est "library". |
| Satellite_Title | .NET | Spécifie une chaîne pour le champ Titre de l'assembly satellite. |
| Satellite_Trademark | .NET | Spécifie une chaîne pour le champ Marque déposée de l'assembly satellite. |
| Satellite_Version | .NET | Spécifie les informations de version concernant l'assembly satellite. |
| Satellite_Win32Icon | .NET | Insère un fichier icône *.ico* dans l’assembly satellite. |
| Satellite_Win32Resource | .NET | Insère une ressource Win32 (fichier *.res*) dans l’assembly satellite. |
| SGenToolPath | .NET | Chemin de l’outil facultatif qui indique où obtenir *SGen.exe* quand la version actuelle de *SGen.exe* est remplacée. |
| SGenUseProxyTypes | .NET | Valeur booléenne qui indique si les types de proxy doivent être générés par *SGen.exe*. Cela s’applique uniquement lorsque *GenerateSerializationAssemblies* a la valeur on.<br /><br /> La cible SGen utilise cette propriété pour définir l'indicateur UseProxyTypes. Cette propriété a true comme valeur par défaut et aucune option d'interface utilisateur ne permet de modifier cela. Pour générer l’assembly de sérialisation pour les types non-webservice, ajoutez cette propriété au fichier projet et affectez-lui la valeur false avant d’importer *Microsoft.Common.Targets* ou *C#/VB.targets*. |
| SkipInvalidConfigurations | Tous | Quand `true` la valeur est, génère un avertissement sur les combinaisons non valides de plateforme et de configuration, mais ne fait pas échouer la build ; lorsque la valeur est ou n’est pas `false` définie (valeur par défaut), génère une erreur. |
| StartupObject | .NET | Spécifie la classe ou le module qui contient la méthode Main ou la procédure Sub Main. Cette propriété est équivalente au commutateur `/main` du compilateur. |
| SubsystemVersion | .NET | Spécifie la version minimale du sous-système utilisable par le fichier exécutable généré. Cette propriété est équivalente au commutateur `/subsystemversion` du compilateur. Pour plus d’informations sur la valeur par défaut de cette propriété, consultez [/subsystemversion (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/subsystemversion) ou [/subsystemversion (options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/subsystemversion-compiler-option). |
| TargetCompactFramework | .NET | Version du .NET Compact Framework requise pour exécuter l'application que vous générez. La spécification de ce paramètre vous permet de référencer certains assemblys Framework que vous ne pourriez peut-être pas référencer autrement. |
| TargetFrameworkVersion | .NET | Version du .NET Framework nécessaire pour exécuter l’application que vous générez. La spécification de ce paramètre vous permet de référencer certains assemblys Framework que vous ne pourriez peut-être pas référencer autrement. |
| TreatWarningsAsErrors | .NET | Paramètre booléen qui, s'il a pour valeur `true`, entraîne le traitement de tous les avertissements comme des erreurs. Ce paramètre est équivalent au commutateur `/nowarn` du compilateur. |
| UseHostCompilerIfAvailable | .NET | Paramètre booléen qui, s'il a pour valeur `true`, force la tâche de génération à utiliser l'objet de compilateur in-process, s'il est disponible. Ce paramètre est utilisé uniquement par Visual Studio. |
| Utf8Output | .NET | Paramètre booléen qui, s'il a pour valeur `true`, consigne la sortie du compilateur en utilisant l'encodage UTF-8. Ce paramètre est équivalent au commutateur `/utf8Output` du compilateur. |
| VbcToolPath | Visual Basic | Chemin facultatif qui indique un autre emplacement pour *vbc.exe* quand la version actuelle de *vbc.exe* est remplacée. |
| VbcVerbosity | Visual Basic | Spécifie le niveau de détail de la sortie du compilateur Visual Basic. Les valeurs valides sont « Quiet », « Normal » (valeur par défaut) et « Verbose ». |
| VisualStudioVersion | Tous | Spécifie la version de Visual Studio dans laquelle ce projet doit être considéré comme s'exécutant. Si cette propriété est omise, MSBuild la définit en tant que valeur par défaut raisonnable.<br /><br /> Cette propriété est utilisée dans plusieurs types de projet pour spécifier l'ensemble des cibles utilisées pour la génération. Si `ToolsVersion` a la valeur 4.0 ou ultérieure pour un projet, `VisualStudioVersion` est utilisé pour spécifier le sous-ensemble d'outils à utiliser. Pour plus d’informations, consultez [Ensemble d’outils (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md). |
| WarningsAsErrors | .NET | Spécifie une liste d'avertissements à traiter comme des erreurs. Ce paramètre est équivalent au commutateur `/warnaserror` du compilateur. |
| WarningsNotAsErrors | .NET | Spécifie une liste d'avertissements à ne pas traiter comme des erreurs. Ce paramètre est équivalent au commutateur `/warnaserror` du compilateur. |
| Win32Manifest | .NET | Nom du fichier manifeste qui doit être incorporé dans l'assembly final. Ce paramètre est équivalent au commutateur `/win32Manifest` du compilateur. |
| Win32Resource | .NET | Nom de fichier de la ressource Win32 à incorporer dans l'assembly final. Ce paramètre est équivalent au commutateur `/win32resource` du compilateur. |

## <a name="see-also"></a>Voir aussi

- [Éléments communs des projets MSBuild](../msbuild/common-msbuild-project-items.md)
