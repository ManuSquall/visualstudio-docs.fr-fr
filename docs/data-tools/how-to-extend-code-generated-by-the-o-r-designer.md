---
title: "Comment : étendre le Code généré par le Concepteur O-R | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d6d1122e-2f55-4607-8d8b-48c3c22600fb
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: cc60c4fe5ff014b1088509c8e5c4982bf7f4322a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-extend-code-generated-by-the-or-designer"></a>Comment : étendre le code généré le Concepteur O/R
Le code généré par le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] est régénéré lorsque des modifications sont apportées aux classes d'entité et autres objets sur l'aire du concepteur. En raison de cette régénération de code par le concepteur, tout code ajouté au code généré est en général remplacé lors de cette opération. Le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] offre la possibilité de générer des fichiers de classe partielle dans lesquels vous pouvez ajouter du code qui ne sera pas remplacé. L'ajout d'une capacité de validation des données à des classes LINQ to SQL (entité) est un exemple d'ajout de code personnel au code généré par le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Pour plus d’informations, consultez [Comment : ajouter une validation aux classes d’entité](../data-tools/how-to-add-validation-to-entity-classes.md).  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="adding-code-to-an-entity-class"></a>Ajout de code à une classe d'entité  
  
#### <a name="to-create-a-partial-class-and-add-code-to-an-entity-class"></a>Pour créer une classe partielle et ajouter du code à une classe d'entité  
  
1.  Ouvrez ou créez un nouveau fichier LINQ to SQL Classes (**.dbml** fichier) dans le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. (Double-cliquez sur le **.dbml** fichier **l’Explorateur de solutions**/**l’Explorateur de base de données**.)  
  
2.  Dans le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], avec le bouton droit de la classe pour laquelle vous souhaitez ajouter la validation, puis cliquez sur **afficher le Code**.  
  
     Une classe partielle pour la classe d'entité sélectionnée s'ouvre dans l'éditeur de code.  
  
3.  Ajoutez votre code dans la déclaration de classe partielle pour la classe d'entité.  
  
## <a name="adding-code-to-a-datacontext"></a>Ajout de code à un DataContext  
  
#### <a name="to-create-a-partial-class-and-add-code-to-a-datacontext"></a>Pour créer une classe partielle et ajouter du code à un DataContext  
  
1.  Ouvrez ou créez un nouveau fichier LINQ to SQL Classes (**.dbml** fichier) dans le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. (Double-cliquez sur le **.dbml** fichier **l’Explorateur de solutions**/**l’Explorateur de base de données**.)  
  
2.  Dans le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], avec le bouton droit sur le Concepteur d’une zone vide, puis sur **afficher le Code**.  
  
     Une classe partielle pour le DataContext s'ouvre dans l'éditeur de code.  
  
3.  Ajoutez votre code dans la déclaration de classe partielle pour le DataContext.  
  
## <a name="see-also"></a>Voir aussi  
 [LINQ to SQL des outils dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Procédure pas à pas : Création des Classes LINQ to SQL (Concepteur O-R)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)   
 [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)   
 