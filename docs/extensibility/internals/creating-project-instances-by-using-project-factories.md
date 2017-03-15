---
title: "Cr&#233;ation d&#39;Instances de projet &#224; l&#39;aide de fabriques de projet | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "fabriques de projet"
  - "fabriques de projet Visual Studio SDK, les projets"
ms.assetid: 94c90012-8669-459c-af8e-307ac242c8c4
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Cr&#233;ation d&#39;Instances de projet &#224; l&#39;aide de fabriques de projet
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Les types de l'utilisation de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]*une fabrique de projet* pour créer des instances d'objets de projet.  Une fabrique de projet est semblable à une fabrique de classe standard pour les objets COM cocreatable.  Toutefois, les objets de projet ne sont pas cocreatable : ils ne peuvent être créés à l'aide d'une fabrique de projet.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE appelle la fabrique de projet implémentée dans votre VSPackage lorsqu'un utilisateur charge un projet existant ou crée un projet dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  Le nouvel objet de projet fournit à l'IDE suffisamment d'informations pour remplir l'explorateur de solutions.  Le nouvel objet de projet fournit également des interfaces requises pour prendre en charge toutes les actions appropriées de l'interface utilisateur effectués par l'IDE.  
  
 vous pouvez implémenter l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> dans une classe dans votre projet.  En général, il réside dans son propre module.  
  
 Pour obtenir un exemple d'implémentation de l'interface d' `IVsProjectFactory` , consultez PrjFac.cpp contenu dans le répertoire de l'exemple de [Basic Project](http://msdn.microsoft.com/fr-fr/385fd2a3-d9f1-4808-87c2-a3f05a91fc36) .  
  
 Les projets qui prennent en charge être regroupé par un propriétaire doivent rendre une clé owner\-drawn dans leur fichier projet.  Lorsque la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> est appelée sur un projet avec une clé owner\-drawn, le projet possédé convertit sa clé de propriétaire à une fabrique GUID de projet appelle ensuite la méthode d' `CreateProject` sur cette fabrique de projet pour effectuer la création réelle.  
  
## créer un projet possédé  
 un propriétaire crée un projet possédé en deux phases :  
  
1.  En appelant la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.PreCreateForOwner%2A>.  Cela permet au projet possédé la possibilité de créer un objet de synthèse de projet basé sur `IUnknown`contrôle d'entrée.  Le projet possédé passe `IUnknown` interne et l'objet regroupé en agrégats de nouveau au projet propriétaire.  Cela permet au projet possédé la possibilité d'enregistrer `IUnknown`interne.  
  
2.  En appelant la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>.  Le projet possédé effectue son instanciation lorsque cette méthode est appelée au lieu d'appeler `IVsProjectFactory::CreateProject` comme est le point de droit pour les projets qui ne sont pas détenus.  l'énumération d' `VSOWNEDPROJECTOBJECT` d'entrée est en général le projet possédé de synthèse.  Le projet possédé peut utiliser cette variable pour déterminer si son objet de projet a déjà été généré \(le cookie n'a pas la valeur NULL\) ou doit être créé \(equals NULL de cookie\).  
  
 Les types de projets sont identifiés par un GUID unique du projet, semblable à le CLSID d'un objet COM cocreatable.  En général, une fabrique de projet gère créer des instances d'un seul type de projet, bien qu'il soit possible d'avoir un type GUID du projet de handle de fabrique de projet plusieurs.  
  
 Les types de projets sont associés à une extension de nom de fichier particulière.  Lorsqu'un utilisateur tente d'ouvrir un fichier projet existant ou essaie de créer un nouveau projet par clonage un modèle, l'IDE utilise l'extension sur le fichier pour déterminer le GUID du projet correspondant.  
  
 Dès que l'IDE détermine s'il doit créer un nouveau projet ou ouvrez un projet existant d'un type particulier, l'IDE utilise les informations de la base de registres sous \[HKEY\_LOCAL\_MACHINE \\Software\\Microsoft\\VisualStudio\\8.0\\Projects\] to find which VSPackage implémente la fabrique requise de projet.  L'IDE charge ce VSPackage.  Dans la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> , le VSPackage doit stocker ses fabriques de projet avec l'IDE en appelant la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes.RegisterProjectType%2A> .  
  
 La méthode principale d'interface d' `IVsProjectFactory` est l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> qui doit gérer deux cas : ouverture d'un projet existant et créer un nouveau projet.  La plupart des projets enregistrent leur état du projet dans un fichier projet.  En général, les nouveaux projets sont créés en faisant une copie du fichier modèle passé à la méthode d' `CreateProject` puis en ouvrant la copie.  Les projets existants sont instanciés en ouvrir directement le fichier projet passé à la méthode d' `CreateProject` .  La méthode d' `CreateProject` peut afficher des fonctionnalités d'interface utilisateur supplémentaires à l'utilisateur si nécessaire.  
  
 Un projet peut également n'utiliser aucun fichier et, à la place, pour stocker son état du projet dans un mécanisme de stockage autre que le système de fichiers, tel qu'une base de données ou un serveur Web.  Dans ce cas, le paramètre de nom de fichier passé à la méthode d' `CreateProject` n'est pas réellement un chemin d'accès de système de fichiers mais une seule chaîne\-un URL\-à identifient les données de projet.  Vous n'avez pas besoin de copier les fichiers modèles qui sont passés à `CreateProject` pour déclencher la séquence correcte de construction pour exécuter.  
  
## Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes>   
 [Liste de vérification : Créer de nouveaux Types de projet](../../extensibility/internals/checklist-creating-new-project-types.md)