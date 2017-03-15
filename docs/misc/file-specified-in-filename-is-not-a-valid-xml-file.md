---
title: "Le fichier sp&#233;cifi&#233; dans FileName n’est pas un fichier XML valide | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c4c30bf3-e0ad-4bc8-89e0-2c3e49e9793b
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le fichier sp&#233;cifi&#233; dans FileName n’est pas un fichier XML valide
Le nom de fichier fourni n’est pas un fichier XML valide. Pour spécifier la structure et le contenu autorisés d’un document XML, vous pouvez utiliser une définition de type de document \(DTD\), un schéma Microsoft XML\-Data Reduced \(XDR\) ou un schéma de langage de définition de schéma XML \(XSD\). Les schémas XSD constituent la meilleure façon de spécifier des grammaires XML dans le [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
> [!NOTE]
>  Dans certaines versions antérieures de Visual Studio, le **Concepteur XML** est le concepteur pour le schéma XML et les datasets typés. Vous pouvez toujours utiliser le **Concepteur XML** pour créer et modifier des fichiers de schéma XML. Toutefois, dans [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)], c’est le **Concepteur de Dataset** qui permet de créer et de modifier des datasets typés. Pour plus d'informations, consultez [Création et modification de Datasets typés](../data-tools/creating-and-editing-typed-datasets.md).  
  
### Pour corriger cette erreur  
  
-   Vérifiez que le nom du fichier que vous fournissez est correct.  
  
-   Vérifiez que le fichier spécifié contient le code XML valide. Pour cela, chargez le fichier XML à vérifier dans le **Concepteur XML**. Dans le menu **XML**, cliquez sur **Valider le XML**. Les erreurs sont répertoriées dans la **Liste des tâches**.  
  
-   Si le fichier XML comprend un schéma XML associé, vérifiez que les éléments apparaissent dans la structure définie et que le contenu de chaque élément est conforme aux types de données déclarés qui sont spécifiés dans le schéma.  
  
## Voir aussi  
 <xref:System.Xml>   
 [Comment : analyser des chemins d'accès](../Topic/How%20to:%20Parse%20File%20Paths%20in%20Visual%20Basic.md)