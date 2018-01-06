---
redirect_url: shell/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file
title: "Modification de l’interpréteur de commandes isolé à l’aide de le. Fichier pkgdef | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio shell, isolated mode, .pkgdef file
ms.assetid: 69e8f78e-bcf1-46cb-8866-7de37d134997
caps.latest.revision: "27"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a0e654e603abe0e4f1546e5b06c2b3644af2067e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="modifying-the-isolated-shell-by-using-the-pkgdef-file"></a>Modification de l’interpréteur de commandes isolé à l’aide de le. Fichier pkgdef
Le fichier .pkgdef prend en charge les paramètres que vous pouvez utiliser pour personnaliser une application de shell isolé. Il spécifie les valeurs qui sont créés lorsqu’une application est installée sur un ordinateur et qui sont référencés par le shell Visual Studio lorsqu’il démarre l’application. Les paramètres sont organisés dans le fichier basé sur les clés de Registre applicable.  
  
> [!WARNING]
>  Notez que les fichiers .pkgdef qui ne sont pas déclarés dans le fichier .vsixmanifest du VSPackage ne sont pas analysés au démarrage de Visual Studio.  
  
 Le fichier .pkgdef contient les sections qui sont chacun identifiées par une clé, soit `[$RootKey$]` ou `[$RootKey$\` *sous-clé*`]`, où $RootKey$ est la clé racine pour l’application.  
  
 Chaque section contient les paires nom/valeur qui ont le format suivant : `"` *ValueName*`"=`*valeur*.  
  
 Les valeurs sont une chaîne placée entre guillemets, ou un entier 32 bits qui est représenté sous la forme d’une valeur dword. Valeurs ont les contraintes suivantes :  
  
-   Toutes les valeurs dword sont au format hexadécimal, par exemple `dword:00000001`.  
  
     Pour les valeurs booléennes, 1 représente true et 0 représente false.  
  
-   Toutes les chaînes GUID sont au format du Registre, par exemple, `"{00000000-0000-0000-0000-000000000000}"`.  
  
-   Tous les identificateurs de ressource localisable ont la forme « @*resourceID*» ou « #*resourceID*», où *resourceID* est l’identificateur de ressource dans le package de l’interface utilisateur d’application par exemple, `"@102"`. Le package de l’interface utilisateur d’application est le package qui est référencé dans le paramètre AppLocalizationPackage.  
  
 Par exemple :  
  
```  
"HideSolutionConcept"=dword:00000001  
"DefaultDebugEngine"="{00000000-0000-0000-0000-000000000000}"  
```  
  
 Vous pouvez ajouter des commentaires dans le fichier .pkgdef. Un commentaire sur une ligne a deux barres obliques dans les deux premiers caractères.  
  
 Pour obtenir la liste des chaînes de substitution, consultez [Substitution chaînes utilisées dans. Pkgdef et. Les fichiers Pkgundef](../extensibility/substitution-strings-used-in-dot-pkgdef-and-dot-pkgundef-files.md).  
  
 Les sections suivantes décrivent les valeurs de Registre spécifiques qui affectent le comportement de l’interpréteur de commandes de Visual Studio en mode isolé. Vous pouvez également définir des valeurs de Registre supplémentaires pour l’application dans ce fichier.  
  
> [!NOTE]
>  Si un paramètre n’est pas fourni dans le fichier .pkgdef, aucune entrée correspondante n’est effectuée dans le Registre.  
  
## <a name="settings"></a>Paramètres  
 Le tableau suivant décrit les valeurs définies sous [$$RootKey].  
  
|Name|Type|Value|  
|----------|----------|-----------|  
|AddinsAllowed|dword|True si les compléments peuvent être chargés ; Sinon, false.<br /><br /> La valeur par défaut est true.|  
|AllowsDroppedFilesOnMainWindow|dword|True si la fenêtre principale peut accepter des fichiers supprimés ; Sinon, false. Supprimé de la fenêtre principale de fichiers sont ouverts à l’aide de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> (méthode). Cela est équivalent à l’ouverture d’un document à l’aide de la **ouvrir** commande sur le **fichier** menu de l’application.<br /><br /> La valeur par défaut est true.|  
|AppIcon|chaîne|Le chemin d’accès complet de l’icône de programme. Cette icône s’affiche dans la barre de titre à gauche du nom de l’application.<br /><br /> La valeur par défaut est « $RootFolder$\\*solutionName*.ico », où *solutionName* est le nom du fichier de solution d’application.|  
|AppLocalizationPackage|chaîne|Le GUID du VSPackage qui contient l’assembly satellite de l’interface utilisateur pour l’application. Ce VSPackage inclut une version compilée du fichier .vsct et permettre inclure d’autres chaînes localisées. Ensembles de fonctionnalités et des groupes de commandes de menu peuvent activés ou désactivés en modifiant les paramètres dans le fichier .vsct de projet l’interface utilisateur.<br /><br /> La valeur par défaut est « {*vsUiPackageGuid*} », où *vsUiPackageGuid* est le GUID affecté au package de l’interface utilisateur d’application.|  
|AppName|chaîne|Nom de l'application. Le nom apparaît dans la barre de titre de la fenêtre d’application.<br /><br /> La valeur par défaut est le nom du fichier de solution d’application.|  
|CommandLineLogo|chaîne|Le texte de bannière lors de l’application est exécutée dans une fenêtre de console. Ce paramètre affecte uniquement les applications qui prennent en charge les opérations de génération de ligne de commande.<br /><br /> La valeur par défaut est «*companyName**solutionName* Version 1.0. », où *companyName* est le nom de la société fourni lors de l’installation de Windows et *solutionName* est le nom du fichier de solution d’application.|  
|DefaultDebugEngine|chaîne|Le GUID de la valeur par défaut du moteur à utiliser pour l’application de débogage.<br /><br /> Remarque : Un GUID vide (zéros) indique que l’application ne spécifie pas un moteur de débogage par défaut. Ainsi, le débogueur sélectionner le moteur de débogage à utiliser.<br /><br /> La valeur par défaut est « {00000000-0000-0000-0000-000000000000} ».|  
|DefaultHomePage|chaîne|L’URL de page d’accueil par défaut de la fenêtre de navigateur Web interne.<br /><br /> Si le **page d’accueil** option est disponible dans l’application, ce paramètre affecte également l’état par défaut de l’option. Pour plus d’informations, consultez [navigateur Web, environnement, boîte de dialogue Options](../ide/reference/web-browser-environment-options-dialog-box.md).<br /><br /> La valeur par défaut est l’URL de la société fournie lors de l’installation de Windows.|  
|DefaultProjectsLocation|chaîne|Le chemin d’accès complet du dossier de projets par défaut. Par exemple :<br /><br /> `"DefaultProjectsLocation"="$MyDocuments$\MyVSShellStub\Projects"`<br /><br /> Si le **emplacement des projets Visual Studio** option est disponible dans l’application, ce paramètre affecte également l’état par défaut de l’option. Pour plus d’informations, consultez [NIB : général, projets et Solutions, boîte de dialogue Options](http://msdn.microsoft.com/en-us/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).<br /><br /> La valeur par défaut est « $MyDocuments$\\*solutionName*», où *solutionName* est le nom du fichier de solution d’application.|  
|DefaultSearchPage|chaîne|URL de page de recherche par défaut pour la fenêtre du navigateur Web interne.<br /><br /> Si le **page de recherche** option est disponible dans l’application, ce paramètre affecte également l’état par défaut de l’option. Pour plus d’informations, consultez [navigateur Web, environnement, boîte de dialogue Options](../ide/reference/web-browser-environment-options-dialog-box.md).<br /><br /> La valeur par défaut est « http://search.live.com ».|  
|DefaultUserFilesFolderRoot|chaîne|Le nom du dossier de l’utilisateur, par rapport à l’utilisateur actuel du dossier Mes Documents.<br /><br /> La valeur par défaut est le nom du fichier de solution d’application.|  
|DisableOutputWindow|dword|Indique si le shell isolé doit traiter la fenêtre de sortie comme étant désactivés.<br /><br /> Si cette valeur est définie sur true, Visual Studio n’affiche pas la sortie de gestionnaire de build de solution dans le **sortie** fenêtre et masque la **afficher la fenêtre Sortie au démarrage de la build** case à cocher dans la  **Projets et Solutions** catégorie dans le **Options** boîte de dialogue.<br /><br /> La valeur par défaut est false.|  
|HideMiscellaneousFilesByDefault|dword|True pour masquer le **fichiers divers** dossier par défaut dans **l’Explorateur de solutions**; sinon, false.<br /><br /> Si le **afficher les fichiers divers dans l’Explorateur de solutions** option est disponible dans l’application, ce paramètre affecte également l’état par défaut de l’option. Pour plus d’informations, consultez [Documents, environnement, boîte de dialogue Options](../ide/reference/documents-environment-options-dialog-box.md).<br /><br /> La valeur par défaut est false.|  
|HideSolutionConcept|dword|True pour créer des projets comme des applications autonomes de tous les projets et de masquer la solution et les commandes d’associés à la solution pour les projets autonomes par défaut ; Sinon, false.<br /><br /> Si le **toujours afficher la solution** option est disponible dans l’application, ce paramètre affecte également l’état par défaut de l’option. Pour plus d’informations, consultez [NIB : général, projets et Solutions, boîte de dialogue Options](http://msdn.microsoft.com/en-us/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).<br /><br /> La valeur par défaut est false.|  
|NewProjDlgInstalledTemplatesHdr|chaîne|Le nom de l’en-tête de modèles Visual Studio nstalled dans les **modèles** liste dans le **nouveau projet** boîte de dialogue. Il s’agit d’une chaîne ou un identificateur de ressource localisable est chargé à partir du package de l’interface utilisateur d’application.<br /><br /> La valeur par défaut est «*solutionName* modèles installés », où *solutionName* est le nom du fichier de solution d’application.|  
|NewProjDlgSlnTreeNodeTitle|chaîne|Le nom de la **Solutions Visual Studio** nœud dans le **types de projet** d’arborescence dans le **nouveau projet** boîte de dialogue. Il s’agit d’une chaîne ou un identificateur de ressource localisable est chargé à partir du package de l’interface utilisateur d’application.<br /><br /> La valeur par défaut est «*solutionName* modèles installés », où *solutionName* est le nom du fichier de solution d’application.|  
|SolutionFileCreatorIdentifier|chaîne|L’identificateur d’application, qui apparaît sous forme de la deuxième ligne dans les fichiers de solution sont générés par l’application. Cette ligne indique à l’application qui a créé le fichier. Par convention, cette valeur comprend le nom de l’application et le numéro de version. Par exemple :<br /><br /> `"SolutionFileCreatorIdentifier"="MyVSShellStub Solution File, Format Version 10.00"`<br /><br /> Le programme VSLauncher.exe, qui est le programme par défaut pour l’ouverture d’un fichier de solution Visual Studio, utilise cette deuxième ligne pour déterminer la version de Visual Studio dans lequel ouvrir le fichier solution. L’application nécessite son propre Lanceur pour gérer ses fichiers de solution associés. Le service de lancement peut également utiliser cette deuxième ligne dans le fichier solution pour déterminer quelle version de l’application pour ouvrir la solution.<br /><br /> Remarque : Le programme Visual Studio VSLauncher.exe ne gère pas les fichiers .sln qui ont été créés par une application de shell isolé.<br /><br /> La valeur par défaut est «*solutionName* fichier de Solution, Version du Format 10,00", où *solutionName* est le nom du fichier de solution d’application.|  
|SolutionFileExt|chaîne|L’extension de nom de fichier de solution pour l’application. Nous vous recommandons de choisir une extension de nom de fichier unique (not.sln).<br /><br /> La valeur par défaut est «*solutionName*_sln », où *solutionName* est le nom du fichier de solution d’application.|  
|SplashScreenBitmap|chaîne|Le chemin d’accès complet du fichier bitmap pour l’écran de démarrage de l’application.<br /><br /> La valeur par défaut est « $RootFolder$\Splash.bmp ».|  
|ThisVersionDTECLSID|chaîne|L’identificateur de classe (CLSID) de l’objet automation de l’application.<br /><br /> L’objet automation de l’application est l’objet de niveau supérieur pour l’application dans le modèle automation de Visual Studio shell et la met en œuvre le <xref:EnvDTE._DTE?displayProperty=fullName> interface.<br /><br /> Si l’objet automation de l’application est correctement inscrit sous la clé de Registre HKEY_CLASSES_ROOT\CLSID, vous pouvez ensuite utiliser le [CComPtrBase::CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance) afin de créer directement une instance de l’application.<br /><br /> L’interpréteur de commandes de Visual Studio utilise ce CLSID pour inscrire l’objet automation de l’application dans la Table ROT (Running Object Table) à l’aide de l’indicateur ACTIVEOBJECT_WEAK. Cela vous permet d’utiliser le [GetActiveObject](http://msdn.microsoft.com/en-us/a276e30c-6a7f-4cde-9639-21a9f5170b62)fonction pour récupérer un pointeur vers une instance en cours d’exécution de l’application. En outre, si vous définissez un ProgID de l’objet automation de l’application, puis le shell Visual Studio enregistre également chaque instance de l’application dans la table ROT à l’aide d’un moniker du formulaire d’élément *progID*:*processID* , où *progID* est le ProgID de l’objet automation d’application, et *processID* est l’identificateur de processus pour cette instance de l’application. Par exemple, si vous créez un moniker comme suit :<br /><br /> `CreateItemMoniker(L"!",`  *instanceString*`, &instanceMoniker)`<br /><br /> où `instanceString` est la *progID*:*processID* chaîne. Ensuite, vous pouvez utiliser `instanceMoniker` avec la fonction GetObject de ROT pour obtenir l’instance.<br /><br /> Si le paramètre ThisVersionDTECLSID est omis, l’application n'est pas exposée via le modèle COM (Component Object). Dans ce cas, une instance de l’application ne peut pas être créée en appelant le [CComPtrBase::CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance) la fonction et ne peut pas être inscrit dans la table ROT.<br /><br /> Chaque version d’un VSPackage doit comporter un CLSID différent.<br /><br /> La valeur par défaut est le GUID généré par Visual Studio pour l’objet automation de l’application.|  
|ThisVersionSolutionCLSID|chaîne|Le CLSID de l’objet de la solution pour l’application.<br /><br /> L’objet automation de solution contient des informations sur la solution actuelle ouverte dans une instance de l’application et l’implémente la <xref:EnvDTE._Solution?displayProperty=fullName> interface.<br /><br /> Si l’objet automation de solution est correctement inscrit sous la clé de Registre HKEY_CLASSES_ROOT\CLSID, vous pouvez ensuite utiliser le [CComPtrBase::CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance) afin de créer directement un objet de la solution pour l’application.<br /><br /> L’interpréteur de commandes de Visual Studio utilise ce CLSID pour inscrire l’objet automation de solution dans la table ROT à l’aide de l’indicateur ACTIVEOBJECT_WEAK.<br /><br /> Si ce paramètre est omis, la classe de solution n’est pas inscrit avec le modèle COM (Component Object), puis un objet de la solution ne peut pas être créé en appelant le [CComPtrBase::CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance) la fonction et ne peut pas être enregistré dans la table ROT.<br /><br /> La valeur par défaut est un GUID généré par Visual Studio pour l’objet de la solution de l’application.|  
|UserFilesSubFolderName|chaîne|Le nom du sous-dossier sous le dossier Mes Documents de l’utilisateur dans lequel l’application crée des sous-dossiers et fichiers utilisateur.<br /><br /> La valeur par défaut est le nom du fichier de solution d’application.|  
|UserOptsFileExt|chaîne|L’extension pour les fichiers options utilisateur de solution pour l’application.<br /><br /> La valeur par défaut est le nom du fichier de solution d’application.|  
  
## <a name="binding-path-settings"></a>Les paramètres de chemin d’accès de liaison  
 Le [$RootKey$ \BindingPaths\\{00000000-0000-0000-0000-000000000000}] clé contient la liste des répertoires dans lesquels l’interpréteur de commandes vérifie les assemblys. Ces répertoires sont ajoutés à la liste des répertoires dans lesquels l’interpréteur de commandes tente de détecter les assemblys privés de l’application.  
  
 Par défaut, aucune entrée de chemin de liaison n’est ajoutées au fichier .pkgdef. Toutefois, les sous-répertoires suivants du répertoire d’installation de Visual Studio sont automatiquement ajoutés à la liste de chemin de liaison d’application dans le Registre.  
  
-   Common7\IDE\  
  
-   Common7\IDE\\\PrivateAssemblies  
  
-   Common7\IDE\\\PublicAssemblies  
  
 Pour ajouter un répertoire pour le chemin de liaison, ajoutez une entrée sous la forme «*Nom_répertoire*« = » », où *Nom_répertoire* est un chemin d’accès absolu. Par exemple :  
  
```  
[$RootKey$\BindingPaths\{00000000-0000-0000-0000-000000000000}]  
"$RootFolder$\directory1"=""  
"%CommonProgramFiles%\directory2"=""  
```  
  
## <a name="profile-settings"></a>Paramètres de profil  
 Le tableau suivant décrit les valeurs qui sont définies pour chaque package associé sous [$RootKey$ \Profile].  
  
|Name|Type|Value|  
|----------|----------|-----------|  
|AutoSaveFile|chaîne|Le répertoire dans lequel l’application stocke les fichiers d’enregistrement automatique.<br /><br /> La valeur par défaut est « $RootFolder$\Profiles\CurrentSettings.vssettings ».|  
  
## <a name="package-satellite-dll-settings"></a>Paramètres de DLL Satellite de package  
 Le tableau suivant décrit les valeurs qui sont définis sous [$RootKey$ \Packages\\{*vsPackageGuid*} \SatelliteDll] pour la DLL de chaque package associé, satellite où *vsPackageGuid* est le GUID du package associé.  
  
|Name|Type|Value|  
|----------|----------|-----------|  
|DllName|chaîne|Le nom de fichier de la DLL.<br /><br /> La valeur par défaut est «*solutionName*ui.dll », où *solutionName* est le nom du fichier de solution d’application.|  
|Chemin d’accès|chaîne|Le répertoire qui contient la DLL satellite.<br /><br /> La valeur par défaut est « $PackageFolder$ ».|  
  
## <a name="package-menu-item-settings"></a>Paramètres de l’élément Menu package  
 La clé de Registre [$RootKey$ \Menus] définit les fichiers de ressources de l’interface utilisateur pour l’application.  
  
 Valeurs d’élément de menu ont la forme « {*vsUiPackageGuid*} « = » *resourceId*, *versionNumber*», où *vsUiPackageGuid* est le GUID de le package de l’interface utilisateur d’application, *resourceId* est l’identificateur de ressource de la ressource CTMENU qui contient les éléments d’interface utilisateur, et *versionNumber* est un numéro de version virtuel pour le CTMENU ressource. Pour plus d’informations, consultez [l’enregistrement de gestionnaires de commandes Assembly Interop](../extensibility/internals/registering-interop-assembly-command-handlers.md).  
  
 Par défaut, une entrée d’élément de menu est créée dans le fichier .pkgdef pour le package de l’interface utilisateur d’application.  
  
 Pour chaque package qui fournit des éléments de menu et qui est distribué dans le cadre de l’application, ajoutez une entrée d’élément de menu pour le package.  
  
## <a name="see-also"></a>Voir aussi  
 [Personnalisation du Shell isolé](../extensibility/customizing-the-isolated-shell.md)   
 [. Fichiers Pkgundef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md)