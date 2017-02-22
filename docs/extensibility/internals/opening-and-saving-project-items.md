---
title: "Ouvrir et enregistrer des &#233;l&#233;ments de projet | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "persistance du fichier Visual Studio SDK, les projets"
  - "fichiers (Visual Studio), ouvrir et enregistrer"
  - "éditeurs (Visual Studio SDK), fichiers de persistance"
ms.assetid: f71898ad-335f-4c43-a177-4da87078afd1
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Ouvrir et enregistrer des &#233;l&#233;ments de projet
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Lorsque vous ajoutez un nouveau type de projet, vous devez gérer l'ouverture et l'enregistrement de vos fichiers dans l'environnement de développement intégré \(IDE\) de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] \(IDE\).  Les rubriques suivantes décrivent les différentes approches à ouvrir et à l'enregistrement de fichiers.  
  
## Dans cette section  
 [Afficher les fichiers à l'aide de la commande Ouvrir un fichier](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)  
 Fournit une explication pas \- à \- pas comment l'IDE gère la commande d' **Ouvrir un fichier** et le rôle des projets pour y répondre à cette commande.  
  
 [Afficher les fichiers à l'aide de l'ouvrir avec la commande](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)  
 Fournit une explication détaillée et pas \- à \- pas comment l'IDE gère la commande d' **Ouvrir avec** , en appelant sur l'ouverture d'un certain tableau des éditeurs standard.  
  
 [Comment : ouvrir les éditeurs spécifiques au projet](../../extensibility/how-to-open-project-specific-editors.md)  
 Fournit des instructions pour spécifier que les fichiers d'un particulier dans votre projet doivent être enregistrés à l'aide d'un éditeur spécifique au projet.  
  
 [Comment : ouvrir les éditeurs Standard](../../extensibility/how-to-open-standard-editors.md)  
 Fournit des instructions pour spécifier comment permettre à l'IDE pour ouvrir un éditeur standard des fichiers dans votre type de projet.  
  
 [Comment : ouvrir des éditeurs pour les Documents ouverts](../../extensibility/how-to-open-editors-for-open-documents.md)  
 Fournit des instructions pas \- à \- pas d'ouvrir un éditeur spécifique aux projets pour un fichier ouvert.  
  
 [Enregistrement d'un Document Standard](../../extensibility/internals/saving-a-standard-document.md)  
 Fournit une explication détaillée de la façon dont l'IDE gère les commandes d' **Enregistrer**, d' **Enregistrer sous**, et d' **Enregistrer tout** pour un document ouvert dans un éditeur standard.  
  
 [Enregistrement d'un Document personnalisé](../../extensibility/internals/saving-a-custom-document.md)  
 Fournit un diagramme et une explication détaillée de la façon dont l'IDE gère les commandes d' **Enregistrer**, d' **Enregistrer sous**, et d' **Enregistrer tout** pour les documents ouverts dans un éditeur personnalisé.  
  
 [Détermination de l'éditeur s'ouvre un fichier dans un projet](../../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)  
 Décrit le processus que l'IDE suivantes pour sélectionner l'éditeur ou le concepteur approprié pour un fichier.  
  
## Rubriques connexes  
 [Création de concepteurs et éditeurs personnalisés](../../extensibility/creating-custom-editors-and-designers.md)  
 Répertorie les quatre types d'éditeur que l'IDE peut héberger et fournit des descriptions de chaque éditeur.  
  
 [Types de projet](../../extensibility/internals/project-types.md)  
 Décrit comment les projets contrôlent la façon dont le code est compilé et créé, comment les éditeurs sont ouverts, et comment les éléments de projet sont mis en forme.