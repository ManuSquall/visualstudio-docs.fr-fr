---
title: 'Comment : ajouter des contrôles XMLNode à des Documents Word | Documents Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNode control, adding to documents
- controls [Office development in Visual Studio], adding to documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4dd214262f66bfa21cdb168e948c70437487761e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-xmlnode-controls-to-word-documents"></a>Comment : ajouter des contrôles XMLNode à des documents Word
  **Important** les informations mentionnées dans cette rubrique concernant Microsoft Word sont présenté exclusivement pour le bénéfice et l’utilisation des personnes et des organisations qui se trouvent en dehors des États-Unis et ses territoires ou qui sont à l’aide d’ou de développement programmes qui s’exécutent sur des produits de Microsoft Word qui ont été concédé sous licence par Microsoft avant de janvier 2010, lorsque Microsoft supprimé une implémentation de fonctionnalités spécifiques liées à XML personnalisées à partir de Microsoft Word. Ces informations concernant Microsoft Word ne peuvent pas lire ou utilisées par des individus ou organisations États-Unis ou dans ses territoires qui utilisent, ou développent des programmes qui s’exécutent sur des produits de Microsoft Word qui ont été concédé sous licence par Microsoft après le 10 janvier 2010 ; ces produits ne comportent pas le même que les produits sous licence avant cette date ou acheté et une licence d’utilisation en dehors des États-Unis.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Lorsque vous mappez un élément de schéma XML non répétitif à un document Microsoft Office Word, Visual Studio ajoute automatiquement un <xref:Microsoft.Office.Tools.Word.XMLNode> contrôle à votre document. Pour plus d’informations sur le mappage des éléments répétés du schéma XML, consultez [Comment : ajouter des contrôles XMLNodes à des Documents Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md).  
  
> [!NOTE]  
>  Le <xref:Microsoft.Office.Tools.Word.XMLNode> contrôle n’est pas disponible à partir de la **boîte à outils** ou **des Sources de données** fenêtre et il ne peut pas être créé par programme.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-add-an-xmlnode-control-to-a-document"></a>Pour ajouter un contrôle XMLNode à un document  
  
1.  Dans le document dans le concepteur Visual Studio, dans le ruban, cliquez sur le **développeur** onglet.  
  
    > [!NOTE]  
    >  Si l'onglet **Développeur** n'est pas visible, vous devez tout d'abord l'afficher. Pour plus d'informations, consultez [Comment : afficher l'onglet Développeur sur le ruban](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
2.  Dans le **XML** , cliquez sur **schéma**.  
  
     Le **modèles et compléments** boîte de dialogue s’ouvre.  
  
3.  Cliquez sur le **schéma XML** onglet.  
  
4.  Cliquez sur **Ajouter schéma**.  
  
     Le **ajouter un schéma** boîte de dialogue s’ouvre.  
  
5.  Sélectionnez un schéma XML qui contient des éléments de schéma non répétitif le **ajouter un schéma** boîte de dialogue et cliquez sur **ouvrir**.  
  
     Le **les paramètres de schéma** boîte de dialogue s’affiche.  
  
6.  Affecter un alias ou cliquez sur **OK** pour ajouter le schéma sans alias.  
  
     Le schéma est ajouté à la **ajouter un schéma** boîte de dialogue.  
  
7.  Dans le **ajouter un schéma** boîte de dialogue, cliquez sur **OK**.  
  
8.  Le **Structure XML** s’ouvre le volet de tâches.  
  
9. Cliquez sur l’élément de schéma non répétitif dans les **Structure XML** volet de tâches pour l’ajouter au document.  
  
     Un <xref:Microsoft.Office.Tools.Word.XMLNode> contrôle est créé et ajouté au projet.  
  
## <a name="see-also"></a>Voir aussi  
 [XMLNode (contrôle)](../vsto/xmlnode-control.md)   
 [Automatisation de Word à l’aide d’objets étendus](../vsto/automating-word-by-using-extended-objects.md)   
 [Vue d'ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)   
 [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  