---
title: 'Procédure : Mapper des schémas à des documents Word dans Visual Studio'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML schemas [Office development in Visual Studio], mapping
- mappings [Office development in Visual Studio], XML schemas to Word documents
- Word [Office development in Visual Studio], mapping XML schemas
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 574f67343bfd2ef7319c1571e84703c4bbf5fe3e
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54867687"
---
# <a name="how-to-map-schemas-to-word-documents-inside-visual-studio"></a>Procédure : Mapper des schémas à des documents Word dans Visual Studio
  **Important** les informations mentionnées dans cette rubrique concernant Microsoft Word sont présentée exclusivement pour le bénéfice et l’utilisation des individus et les organisations qui se trouvent en dehors des États-Unis et ses territoires ou qui utilisent ou développement les programmes qui s’exécutent sur des produits de Microsoft Word qui ont été concédés sous licence par Microsoft avant janvier 2010, lorsque Microsoft supprimé une implémentation de fonctionnalités spécifiques liés à XML personnalisé à partir de Microsoft Word. Ces informations concernant Microsoft Word ne peuvent pas être lues ou utilisées par les individus ou organisations dans les États-Unis ou dans ses territoires qui sont à l’aide d’ou de développer des programmes qui s’exécutent sur des produits de Microsoft Word qui ont été concédés sous licence par Microsoft après le 10 janvier 2010 ; ces produits ne comportent pas le même que les produits sous licence avant cette date ou acheté et concédés sous licence pour une utilisation en dehors des États-Unis.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Vous pouvez mapper un schéma XML à un document pendant que le document est ouvert dans Visual Studio. Vous utilisez les mêmes outils de Microsoft Office Word que vous utilisez lorsque le document est ouvert en dehors de Visual Studio. Le projet Office crée les mêmes objets que vous mappiez le schéma pour le document avant ou après avoir créé votre solution Word.  
  
## <a name="to-map-an-xml-schema-to-a-word-document-in-visual-studio"></a>Pour mapper un schéma XML à un document Word dans Visual Studio  
  
1.  Ouvrez le projet de document ou modèle Word dans Visual Studio.  
  
2.  Cliquez dans le document pour déplacer le focus vers le concepteur.  
  
3.  Dans le ruban, cliquez sur le **développeur** onglet.  
  
    > [!NOTE]  
    >  Si l'onglet **Développeur** n'est pas visible, vous devez tout d'abord l'afficher. Pour plus d'informations, voir [Procédure : Afficher l’onglet Développeur sur le ruban](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
4.  Dans le **XML** de groupe, cliquez sur **schéma**.  
  
     Le **modèles et compléments** boîte de dialogue s’ouvre.  
  
5.  Cliquez sur le **schéma XML** onglet.  
  
6.  Cliquez sur **Ajouter schéma**.  
  
     Le **ajouter un schéma** boîte de dialogue s’ouvre.  
  
7.  Accédez à votre fichier de schéma, sélectionnez-le, puis cliquez sur **Open**.  
  
     Le **les paramètres de schéma** boîte de dialogue s’ouvre.  
  
8.  Affecter un alias ou cliquez sur **OK** pour ajouter le schéma sans alias.  
  
9. Cliquez sur **OK**.  
  
     Le **Structure XML** fenêtre s’ouvre.  
  
10. Faire glisser des éléments à partir de la **Structure XML** fenêtre aux endroits de votre document où vous souhaitez que les contrôles correspondants à créer.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour Mapper des schémas à des feuilles de calcul à l’intérieur de Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)   
 [Schémas XML et des données dans les personnalisations au niveau du document](../vsto/xml-schemas-and-data-in-document-level-customizations.md)  
