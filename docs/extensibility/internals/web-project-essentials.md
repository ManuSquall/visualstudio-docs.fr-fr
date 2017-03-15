---
title: "Web Essentials de projet | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "projets Web, essentials"
ms.assetid: ca2f4e43-322c-4431-8680-52da846940bc
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Web Essentials de projet
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Projets Web créent des applications Web. Vous pouvez utiliser un projet Web pour créer une application Web qui a des pages Web actives. Une page Web active comporte du code côté serveur qui affiche la page Web à la demande.  
  
 À l’aide de langages de programmation traditionnels, tels que [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] ou [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], vous pouvez créer des pages Web actives pour collecter et traiter les informations d’un utilisateur, stockez-le dans une base de données et ainsi de suite.  
  
-   Le modèle code-behind associe les fichiers de code source dépendant des pages Web .asmx ou .aspx d’extension de fichier. Par exemple, hello.aspx peut avoir le hello.aspx.cs de fichier de code source dépendant.  
  
-   Le code côté serveur associé à une page Web active est compilé dans un fichier exécutable qui se trouve dans le dossier /bin de site Web.  
  
-   Fichiers de code source supplémentaires, tels que les classes d’assistance qui ne sont pas associés à une page Web spécifique, se trouvent dans le dossier/App_Code du site Web.  
  
    -   Un projet de site Web (WSP) génère un fichier exécutable pour chaque page Web active. Fichiers exécutables supplémentaires sont générés à partir des fichiers de code source dans le dossier/App_Code.  
  
    -   Un projet d’application Web (WAP) produit un fichier exécutable qui combine le code pour toutes les pages Web actives, ainsi que tous les fichiers source dans le dossier/App_Code.  
  
-   Le fichier de solution pour un projet Web se trouve séparément à partir du site Web lui-même. Par défaut, les fichiers solution sont situées dans \Documents and Settings\\*VotreCompte*\My Documents\\*\< Visual Studio ### >*\Projects\\*votresiteweb*.  
  
    > [!NOTE]
    >  Si vous souhaitez conserver le fichier de solution avec le site Web, déplacez simplement d’il et rouvrez-le.  
  
-   Si vous ouvrez un site Web qui ne contient aucun fichier solution dans Visual Studio, un nouveau fichier de solution est automatiquement généré pour lui.  
  
-   Les projets Web ne contiennent aucun fichier projet. Les informations de projet sont stockées dans le fichier solution, le fichier web.config et ailleurs.  
  
-   Ajout automatique de propriétés globales à un projet Web crée un fichier de stockage dans le dossier de solution du projet Web.  
  
-   Une page Web active peut être associée à un langage de programmation côté serveur en utilisant la directive de Page ou \< script runat = « server »> tag.  
  
-   En outre, les pages Web peuvent avoir n’importe quel nombre de blocs de scripts côté client écrit dans n’importe quel langage de script.  
  
-   Un système de projet de site Web est implémenté en ajoutant des modèles de projet et d’élément et de l’inscription à la [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] projet.  
  
-   Un système WAP est implémenté comme un sous-type de projet, également appelé une version de projet. Le [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] est versionné de projet par le sous-type WAP pour créer le système WAP. Pour plus d’informations sur les sous-types de projets, consultez [sous-types de projets](../../extensibility/internals/project-subtypes.md).  
  
-   Une page Web active combine HTML avec un langage de programmation côté serveur. Le langage côté serveur est qualifié de langage de relation contenant-contenu. Pour prendre en charge un langage de relation contenant-contenu, le système de projet Web doit implémenter le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> famille d’interfaces.  
  
    -   Pour prendre en charge la langue contenue dans un éditeur, le service de langage HTML doit différer l’affichage du code de langue de relation contenant-contenu pour un service de langage de relation contenant-contenu.  
  
    -   Marqueurs d’erreur (tildes rouges) doivent toujours être créés dans la mémoire tampon principale de l’éditeur de code.  
  
## <a name="see-also"></a>Voir aussi  
 [Projets Web](../../extensibility/internals/web-projects.md)