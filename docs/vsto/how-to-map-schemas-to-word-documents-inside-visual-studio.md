---
title: "Comment : mapper des schémas à des Documents Word dans Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML schemas [Office development in Visual Studio], mapping
- mappings [Office development in Visual Studio], XML schemas to Word documents
- Word [Office development in Visual Studio], mapping XML schemas
ms.assetid: 9bfb3c7b-6392-45bd-b4c1-b2012b9ded69
caps.latest.revision: "27"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: fdfc13415a06960ad0ec736b19eb5b2483e7f19c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-map-schemas-to-word-documents-inside-visual-studio"></a>Comment : mapper des schémas à des documents Word dans Visual Studio
  **Important** les informations mentionnées dans cette rubrique concernant Microsoft Word sont présenté exclusivement pour le bénéfice et l’utilisation des personnes et des organisations qui se trouvent en dehors des États-Unis et ses territoires ou qui sont à l’aide d’ou de développement programmes qui s’exécutent sur des produits de Microsoft Word qui ont été concédé sous licence par Microsoft avant de janvier 2010, lorsque Microsoft supprimé une implémentation de fonctionnalités spécifiques liées à XML personnalisées à partir de Microsoft Word. Ces informations concernant Microsoft Word ne peuvent pas lire ou utilisées par des individus ou organisations États-Unis ou dans ses territoires qui utilisent, ou développent des programmes qui s’exécutent sur des produits de Microsoft Word qui ont été concédé sous licence par Microsoft après le 10 janvier 2010 ; ces produits ne comportent pas le même que les produits sous licence avant cette date ou acheté et une licence d’utilisation en dehors des États-Unis.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Vous pouvez mapper un schéma XML à un document lorsque le document est ouvert dans Visual Studio. Vous utilisez les mêmes outils Microsoft Office Word que vous utilisez lorsque le document est ouvert en dehors de Visual Studio. Le projet Office crée les mêmes objets que vous mappiez le schéma au document avant ou après avoir créé votre solution Word.  
  
### <a name="to-map-an-xml-schema-to-a-word-document-in-visual-studio"></a>Pour mapper un schéma XML à un document Word dans Visual Studio  
  
1.  Ouvrez le projet de document ou un modèle Word dans Visual Studio.  
  
2.  Cliquez dans le document pour déplacer le focus vers le concepteur.  
  
3.  Dans le ruban, cliquez sur l'onglet **Développeur** .  
  
    > [!NOTE]  
    >  Si l'onglet **Développeur** n'est pas visible, vous devez tout d'abord l'afficher. Pour plus d'informations, consultez [How to: Show the Developer Tab on the Ribbon](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
4.  Dans le **XML** , cliquez sur **schéma**.  
  
     Le **modèles et compléments** boîte de dialogue s’ouvre.  
  
5.  Cliquez sur le **schéma XML** onglet.  
  
6.  Cliquez sur **Ajouter schéma**.  
  
     Le **ajouter un schéma** boîte de dialogue s’ouvre.  
  
7.  Accédez à votre fichier de schéma, sélectionnez-le, puis cliquez sur **ouvrir**.  
  
     Le **les paramètres de schéma** boîte de dialogue s’ouvre.  
  
8.  Affecter un alias ou cliquez sur **OK** pour ajouter le schéma sans alias.  
  
9. Cliquez sur **OK**.  
  
     Le **Structure XML** fenêtre s’ouvre.  
  
10. Faire glisser des éléments à partir de la **Structure XML** fenêtre aux endroits de votre document où vous souhaitez que les contrôles correspondants à créer.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : mapper des schémas à des feuilles de calcul à l’intérieur de Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)   
 [Schémas et données XML dans les personnalisations au niveau du document](../vsto/xml-schemas-and-data-in-document-level-customizations.md)  
  
  