---
title: "Comment : activer et désactiver (Concepteur O-R) pluralisation | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 87779cb647e00c990f4f8b29907a0dc344b80f42
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>Comment : activer et désactiver (Concepteur O/R) pluralisation
Par défaut, lorsque vous faites glisser des objets de base de données qui ont des noms se terminant par s ou ies de **l’Explorateur de serveurs**/**l’Explorateur de base de données** sur la [LINQ to SQL Tools dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md), les noms des classes d’entité générés sont modifiés au pluriel au singulier. C'est pour insister sur le fait que la classe d'entité instanciée mappe à un enregistrement unique de données. Par exemple, l'ajout d'une table Customers au [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] génère une classe d'entité nommée Customer parce que la classe gérera les données d'un seul client.  
  
> [!NOTE]
>  Par défaut, la pluralisation est activée uniquement dans la version de langue anglaise de Visual Studio.  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### <a name="to-turn-pluralization-on-and-off"></a>Pour activer et désactiver la pluralisation  
  
1.  Dans le menu **Outils** , cliquez sur **Options**.  
  
2.  Dans le **Options** boîte de dialogue, développez **outils de base de données**.  
  
    > [!NOTE]
    >  Sélectionnez **afficher tous les paramètres** si le **outils de base de données** nœud n’est pas visible.  
  
3.  Cliquez sur **Concepteur O/R**.  
  
4.  Définissez **Pluralisation des noms** à **activé** = **False** pour définir le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] afin qu’il ne modifie pas les noms de classe.  
  
5.  Définissez **Pluralisation des noms** à **activé** = **True** pour appliquer des règles de pluralisation aux noms de classes d’objets ajoutés à la [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
## <a name="see-also"></a>Voir aussi  
[LINQ to SQL des outils dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
[LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)   
[Accès aux données dans Visual Studio](../data-tools/accessing-data-in-visual-studio.md)