---
title: Web Essentials du projet | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: web projects, essentials
ms.assetid: ca2f4e43-322c-4431-8680-52da846940bc
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ac781256ee78becf3b0cfdffbbec6f0c6bc30225
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="web-project-essentials"></a>Essentials du projet Web
Projets Web créent des applications Web. Vous pouvez utiliser un projet Web pour créer une application Web qui a des pages Web actives. Une page Web active a le code côté serveur qui restitue la page Web à la demande.  
  
 À l’aide des langages de programmation traditionnels, tels que [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] ou [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], vous pouvez créer des pages Web actives pour collecter et traiter les informations à partir d’un utilisateur, stockez-le dans une base de données et ainsi de suite.  
  
-   Le modèle code-behind associe les fichiers de code source dépendant des pages Web qui ont le fichier extension .aspx ou .asmx. Par exemple, hello.aspx peut avoir le hello.aspx.cs de fichier de code source dépendant.  
  
-   Le code côté serveur associé à une page Web active est compilé dans un fichier exécutable qui se trouve dans le dossier/Bin du site Web.  
  
-   Fichiers de code source supplémentaires, tels que les classes d’assistance qui ne sont pas associés à une page Web spécifique, se trouvent dans le site Web le dossier.  
  
    -   Un projet de site Web (WSP) génère un fichier exécutable pour chaque page Web active. Fichiers exécutables supplémentaires sont générés à partir de tous les fichiers de code source dans le dossier/App_Code.  
  
    -   Un projet d’application Web (WAP) produit un seul fichier exécutable qui combine le code pour toutes les pages Web actives, ainsi que tous les fichiers sources dans le dossier/App_Code.  
  
-   Le fichier de solution pour un projet Web se trouve séparément à partir du site Web lui-même. Par défaut, les fichiers solution sont situées dans \Documents and Settings\\*VotreCompte*\My Documents\\*\<Visual Studio ### >*\Projects\\ *Votresiteweb*.  
  
    > [!NOTE]
    >  Si vous souhaitez conserver le fichier de solution avec le site Web, déplacez-y simplement et le rouvrir.  
  
-   Si vous ouvrez un site Web qui n’a aucun fichier de solution dans Visual Studio, un nouveau fichier de solution est automatiquement généré pour celui-ci.  
  
-   Les projets Web ne contenir aucun fichier projet. Les informations de projet sont stockées dans le fichier solution, le fichier web.config et ailleurs.  
  
-   Ajouter automatiquement des propriétés globales à un projet Web pour créer un fichier de stockage dans le dossier de solution du projet Web.  
  
-   Une page Web active peut être associée à un langage de programmation côté serveur à l’aide de la directive de Page ou le \<script runat = « server » > balise.  
  
-   En outre, les pages Web peuvent avoir n’importe quel nombre de blocs de scripts côté client écrit dans n’importe quel langage de script.  
  
-   Un système de projet de site Web est implémenté en ajoutant des modèles de projet et d’élément et de l’inscription à la [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] projet.  
  
-   Un système WAP est implémenté comme un sous-type de projet, également appelé une version de projet. Le [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] projet est flavored par le sous-type de proxy d’application Web pour créer le système WAP. Pour plus d’informations sur les sous-types de projet, consultez [sous-types de projet](../../extensibility/internals/project-subtypes.md).  
  
-   Une page Web active combine HTML avec un langage de programmation côté serveur. Le langage côté serveur est appelé le langage de relation contenant-contenu. Pour prendre en charge un langage de relation contenant-contenu, le système de projet Web doit implémenter la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> famille d’interfaces.  
  
    -   Pour prendre en charge la langue contenue dans un éditeur, le service de langage HTML doit différer l’affichage de code de langue de la relation contenant-contenu pour un service de langage de relation contenant-contenu.  
  
    -   Marqueurs d’erreur (rouge tildes) doivent toujours être créés dans la mémoire tampon principale de l’éditeur de code.  
  
## <a name="see-also"></a>Voir aussi  
 [Projets Web](../../extensibility/internals/web-projects.md)