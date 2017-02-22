---
title: "Options, &#201;diteur de texte, Extension de fichier | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.toolsoptionspages.text_editor.file_extension"
helpviewer_keywords: 
  - "extensions de fichier, association à l’éditeur"
  - "Éditeur choisi"
  - "Options (boîte de dialogue)"
  - "Éditeur choisi, sélection"
ms.assetid: 05298fc5-fc4e-4bb2-b942-1f7d2dcdff0f
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# Options, &#201;diteur de texte, Extension de fichier
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Cette boîte de dialogue Options permet de spécifier comment tous les fichiers avec une extension donnée seront gérés par l'environnement de développement intégré Visual Studio \(IDE\).  Pour chaque **Extension** que vous entrez, vous pouvez sélectionner un éditeur.  Cela vous permet de choisir l'éditeur IDE ou le concepteur dans lequel les documents d'un certain type s'ouvriront.  Pour afficher ces options, choisissez **Options** dans le menu **Outils**, développez le nœud **Éditeur de texte**, et sélectionnez **Extension de fichier**.  
  
 Lorsque vous sélectionnez une option "avec encodage", une boîte de dialogue s'affiche chaque fois que vous ouvrez un document de ce type et vous permet de sélectionner une méthode de codage pour le document.  Ce comportement peut être utile si vous préparez des versions de vos documents de projet pour les utiliser sur différentes plateformes ou dans des langues cible différentes.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Liste UIElement  
 **Extension**  
 Tapez l'extension de fichier pour laquelle vous souhaitez définir un Éditeur choisi dans l'IDE.  
  
 **Éditeur**  
 Sélectionnez l'éditeur IDE ou le concepteur dans lequel les documents avec cette extension de fichier s'ouvriront.  Lorsque vous sélectionnez une option "avec encodage", une boîte de dialogue s'affiche chaque fois que vous ouvrez un document et vous permet de sélectionner un schéma de codage.  
  
 **Ajouter**  
 Ajoute à la liste des extensions une entrée qui inclut l'**Extension** spécifiée et l'**Éditeur choisi**.  
  
 **Supprimer**  
 Supprime l'entrée sélectionnée de la liste des extensions.  
  
 Liste d'extensions  
 Répertorie toutes les extensions pour lesquelles un Éditeur choisi a été spécifié.  
  
 **Mapper les fichiers sans extension vers**  
 Sélectionnez cette option si vous souhaitez spécifier comment les fichiers sans extension doivent être gérés par l'IDE.  
  
 **Options des fichiers sans extensions**  
 Fournit la même liste qu'**Éditeur**.  Sélectionnez l'éditeur IDE ou le concepteur dans lequel les documents sans extensions de fichier s'ouvriront.  
  
## Voir aussi  
 [Comment : gérer les modes de l'éditeur](../../ide/how-to-manage-editor-modes.md)