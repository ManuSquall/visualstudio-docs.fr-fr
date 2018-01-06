---
title: "La gestion des Associations de fichiers de côte-à-côte | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: verbs, setting default
ms.assetid: 9b6df3bc-d15c-4a5d-9015-948a806193b7
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7d0a6f8ec88a49b785b771aef51dc25b5646ffda
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="managing-side-by-side-file-associations"></a>La gestion des Associations de fichiers de côte à côte
Si votre VSPackage fournit des associations de fichiers, vous devez décider comment gérer des installations côte à côte dans lesquels une version particulière de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] doit être appelé pour ouvrir un fichier. Formats de fichier incompatibles composés le problème.  
  
 Les utilisateurs attendent une nouvelle version d’un produit pour être compatible avec les versions antérieures, afin que les fichiers existants peuvent être chargés dans une nouvelle version sans perte de données. Dans l’idéal, votre VSPackage peut charger et enregistrer les formats de fichier des versions antérieures. Si tel n’est pas vrai, vous pouvez proposer mettre à niveau le format de fichier pour la nouvelle version de votre VSPackage. L’inconvénient de cette approche est que le fichier mis à niveau ne peut pas être ouvert dans une version antérieure.  
  
 Pour éviter ce problème, vous pouvez modifier des extensions lorsque les formats de fichier sont incompatibles. Par exemple, la version 1 de votre VSPackage peut utiliser l’extension, le .mypkg10 et la version 2 peut utiliser l’extension, .mypkg20. Cette différence identifie le VSPackage qui ouvre un fichier particulier. Si vous ajoutez des VSPackages plus récente à la liste des programmes qui sont associés à une ancienne extension, les utilisateurs peuvent clic droit sur le fichier et choisissez Ouvrir dans un VSPackage plus récente. À ce stade, votre VSPackage peut offrir à mettre à niveau le fichier vers le nouveau format ou ouvrez le fichier et assurer la compatibilité avec les versions antérieures du VSPackage.  
  
> [!NOTE]
>  Vous pouvez combiner ces deux approches. Par exemple, vous pouvez offrent une compatibilité descendante en chargeant un fichier plus ancien et mettre à niveau le format de fichier lorsque l’utilisateur enregistre.  
  
## <a name="facing-the-problem"></a>Le problème d’accès au  
 Si vous souhaitez que plusieurs VSPackages côte à côte pour utiliser la même extension, vous devez choisir la version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] qui est associé à l’extension. Voici deux possibilités :  
  
-   Ouvrez le fichier dans la version la plus récente de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] installé sur l’ordinateur d’un utilisateur.  
  
     Dans cette approche, votre programme d’installation est responsable de la détermination de la dernière version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et y compris celui de l’entrée de Registre écrite pour l’association de fichiers. Dans un package Windows Installer, vous pouvez inclure des actions personnalisées pour définir une propriété qui indique la dernière version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
    > [!NOTE]
    >  Dans ce contexte, « dernier » signifie « version la plus récente. » Ces entrées de programme d’installation ne détecte pas automatiquement une version ultérieure de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Entrées dans [détection configuration système requise du](../extensibility/internals/detecting-system-requirements.md) et dans [commandes que doit être exécuté après l’Installation du](../extensibility/internals/commands-that-must-be-run-after-installation.md) sont semblables à celles présentées ici et sont requises pour prendre en charge des versions supplémentaires de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
     Les lignes suivantes dans la table CustomAction définir la propriété DEVENV_EXE_LATEST une propriété définie par l’AppSearch et RegLocator tables décrits dans [commandes que doit être exécuté après l’Installation](../extensibility/internals/commands-that-must-be-run-after-installation.md). Lignes de la table InstallExecuteSequence planifier les actions personnalisées au début de la séquence d’exécution. Valeurs de la marque de colonne Condition la logique de travail :  
  
    -   Visual Studio .NET 2002 est la version la plus récente s’il s’agit de la version actuelle uniquement.  
  
    -   Visual Studio .NET 2003 est la dernière version uniquement s’il est présent et [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] n’est pas présent.  
  
    -   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]est la version la plus récente s’il s’agit de la version actuelle uniquement.  
  
     Le résultat net est que DEVENV_EXE_LATEST contient le chemin d’accès de la dernière version de devenv.exe.  
  
    ### <a name="customaction-table-rows-that-determine-the-latest-version-of-visual-studio"></a>Lignes de la table CustomAction qui déterminent la version la plus récente de Visual Studio  
  
    |Action|Type|Source|une cible|  
    |------------|----------|------------|------------|  
    |CA_SetDevenvLatest_2002|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2002]|  
    |CA_SetDevenvLatest_2003|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2003]|  
    |CA_SetDevenvLatest_2005|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2005]|  
  
    ### <a name="installexecutesequence-table-rows-that-determine-the-latest-version-of-visual-studio"></a>Lignes de la table InstallExecuteSequence qui déterminent la version la plus récente de Visual Studio  
  
    |Action|Condition|Séquence|  
    |------------|---------------|--------------|  
    |CA_SetDevenvLatest_2002|DEVENV_EXE_2002 ET NON (DEVENV_EXE_2003 OU DEVENV_EXE_2005)|410|  
    |CA_SetDevenvLatest_2003|DEVENV_EXE_2003 ET PAS DEVENV_EXE_2005|420|  
    |CA_SetDevenvLatest_2005|DEVENV_EXE_2005|430|  
  
     Vous pouvez utiliser la propriété DEVENV_EXE_LATEST dans la table de Registre du package Windows Installer pour écrire le HKEY_CLASSES_ROOT*ProgId*valeur par défaut de la clé ShellOpenCommand [DEVENV_EXE_LATEST] « %1 »  
  
-   Exécuter un programme de lancement partagé qui peut rendre le meilleur choix à partir de versions VSPackage disponibles.  
  
     Les développeurs de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] choisi cette approche pour gérer les exigences complexes des plusieurs formats de solutions et projets qui résultent de nombreuses versions de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Dans cette approche, vous inscrivez un programme de lancement en tant que le Gestionnaire d’extensions. Le service de lancement examine le fichier et détermine la version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et votre VSPackage peut gérer ce fichier particulier. Par exemple, si un utilisateur ouvre un fichier qui a été enregistré dans une version particulière de votre VSPackage, le service de lancement peut démarrer que VSPackage dans la version correspondante de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. En outre, un utilisateur peut configurer le service de lancement pour toujours démarrer la version la plus récente. Un lanceur également pu inviter un utilisateur à mettre à niveau le format du fichier. Si le format du fichier inclut un numéro de version, le service de lancement peut informer un utilisateur si le format de fichier provient d’une version ultérieure à une ou plusieurs des VSPackages installés.  
  
     Le service de lancement doit être dans un composant de Windows Installer est partagé avec toutes les versions de votre VSPackage. Ce processus permet de s’assurer que la version la plus récente est toujours installée et qu’il n’est pas supprimée tant que toutes les versions de votre VSPackage sont désinstallées. De cette façon, les associations de fichiers et d’autres entrées de Registre du composant Lanceur sont conservées même si une version du VSPackage est désinstallée.  
  
## <a name="uninstall-and-file-associations"></a>Désinstaller et les Associations de fichiers  
 Un VSPackage qui écrit des entrées de Registre pour les associations de fichiers en désinstallant les associations de fichiers. Par conséquent, l’extension ne possède aucun programme n’est associé. Windows Installer ne pas « recover » les entrées de Registre qui ont été ajoutées lors de l’installation le VSPackage. Voici quelques méthodes permettant de corriger les associations de fichiers d’un utilisateur :  
  
-   Utiliser un composant partagé Lanceur comme décrit précédemment.  
  
-   Demandez à l’utilisateur à exécuter une réparation de la version du VSPackage que l’utilisateur souhaite qu’il possède l’association de fichiers.  
  
-   Fournir un programme exécutable qui réécrit les entrées de Registre appropriées.  
  
-   Fournir une configuration options page ou boîte de dialogue qui permet aux utilisateurs de choisir les associations de fichiers et de récupérer des associations perdues. Demandez aux utilisateurs pour l’exécuter après la désinstallation.  
  
## <a name="see-also"></a>Voir aussi  
 [L’inscription des Extensions de nom de fichier pour les déploiements côte à côte](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [Inscription des verbes pour les extensions de nom de fichier](../extensibility/registering-verbs-for-file-name-extensions.md)