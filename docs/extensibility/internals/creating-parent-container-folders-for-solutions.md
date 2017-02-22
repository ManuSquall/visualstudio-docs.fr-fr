---
title: "Cr&#233;ation de dossiers de conteneur Parent pour les Solutions | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "solutions de création de conteneurs parents"
  - "contrôle plug-ins de source, création de conteneurs parents"
ms.assetid: 961e68ed-2603-4479-a306-330eda2b2efa
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Cr&#233;ation de dossiers de conteneur Parent pour les Solutions
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Dans la version du plug\-in 1,2 d'API de contrôle de code source, un utilisateur peut spécifier une destination unique de contrôle de code source racine pour tous les projets Web dans la solution.  Cette racine unique est appelée une racine unifiée super \(SUR\).  
  
 Dans la version du plug\-in 1,1 d'API de contrôle de code source, si l'utilisateur ajoutait une solution de multiproject au contrôle de code source, l'utilisateur a été invité à spécifier une destination de contrôle de code source pour chaque projet Web.  
  
## nouvelles balises de fonction  
 `SCC_CAP_CREATESUBPROJECT`  
  
 `SCC_CAP_GETPARENTPROJECT`  
  
## nouvelles fonctions  
 [SccCreateSubProject](../../extensibility/scccreatesubproject-function.md)  
  
 [SccGetParentProjectPath](../../extensibility/sccgetparentprojectpath-function.md)  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l'IDE crée presque toujours un dossier de SUR en ajoutant une solution au contrôle de code source.  Spécifiquement, il le fait dans les cas suivants :  
  
-   le projet est un projet Web de partage de fichiers.  
  
-   Il existe différents lecteurs pour le projet et le fichier solution.  
  
-   Il existe plusieurs partages pour le projet et le fichier solution.  
  
-   Les projets ont été ajoutés séparément \(dans une solution exemple\).  
  
 Dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] on suggère que le nom du dossier de SUR soit identique au nom de la solution sans l'extension.  le tableau suivant résume le comportement dans les deux versions.  
  
|Fonctionnalité|version du plug\-in du contrôle 1,1 d'API tSource|Version du plug\-in 1,2 d'API de contrôle de code source|  
|--------------------|-------------------------------------------------------|--------------------------------------------------------------|  
|Ajouter la solution au SCC|SccInitialize\(\)<br /><br /> SccGetProjPath\(\)<br /><br /> SccGetProjPath\(\)<br /><br /> SccOpenProject\(\)|SccInitialize\(\)<br /><br /> SccGetProjPath\(\)<br /><br /> SccCreateSubProject\(\)<br /><br /> SccCreateSubProject\(\)<br /><br /> SccOpenProject\(\)|  
|Ajoutez le projet à la solution exemple|SccGetProjPath\(\)<br /><br /> OpenProject\(\)|SccGetParentProjectPath\(\)<br /><br /> SccOpenProject\(\) **Note:**  Visual Studio suppose qu'une solution est un enfant direct du SUR.|  
  
## Exemples  
 Le tableau suivant répertorie deux exemples.  Dans les deux cas, l'utilisateur de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] est invité à spécifier un emplacement de destination pour la solution sous contrôle de code source jusqu'à ce qu'*user\_choice* soit spécifié comme destination. Lorsque l'user\_choice est spécifié, la solution et deux projets sont ajoutés sans inviter l'utilisateur à des destinations de contrôle de code source.  
  
|la solution contient|Sur les emplacements de disque|Structure par défaut de base de données|  
|--------------------------|------------------------------------|---------------------------------------------|  
|sln1.sln<br /><br /> Web1<br /><br /> Web2|C : \\Solutions \\ sln1<br /><br /> C : \\Inetpub\\wwwroot\\Web 1<br /><br /> \\ \\ serveur \\ wwwroot$ \\ web2|$*user\_choice*\/sln1<br /><br /> $*user\_choice*\/C\/Web1<br /><br /> $*user\_choice*\/Web2|  
|sln1.sln<br /><br /> Web1<br /><br /> Win1|C : \\Solutions \\ sln1<br /><br /> d : \\Inetpub\\wwwroot\\Web 1<br /><br /> C : \\solutions\\sln1\\Win 1|$*user\_choice*\/sln1<br /><br /> $*user\_choice*\/D\/web1<br /><br /> $*user\_choice*\/sln1\/win1|  
  
 Le dossier et des sous\-dossiers de SUR sont créés que l'opération est annulée ou échoue en raison d'une erreur.  Ils ne sont pas automatiquement supprimés dans l'annulation ou des conditions d'erreur.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a comme valeur par défaut le comportement de la version 1,1 si le plug\-in contrôle de code source ne retourne pas `SCC_CAP_CREATESUBPROJECT` et des balises de fonction d' `SCC_CAP_GETPARENTPROJECT` .  En outre, les utilisateurs de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] peuvent choisir de rétablir le comportement de la version 1,1 en définissant la valeur de la clé suivante à dword : 00000001 :  
  
 \[\=dword HKEY\_CURRENT\_USER \\Software\\Microsoft\\VisualStudio\\8.0\\SourceControl\] "DoNotCreateSolutionRootFolderInSourceControl " : 00000001  
  
## Voir aussi  
 [Quelles sont les nouveautés dans la Source contrôle plug\-in API Version 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)