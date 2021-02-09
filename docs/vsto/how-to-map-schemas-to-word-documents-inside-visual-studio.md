---
title: 'Comment : mapper des schémas à des documents Word dans Visual Studio'
description: Découvrez comment mapper un schéma XML à un document Word Microsoft Office pendant que le document est ouvert dans Visual Studio.
titleSuffix: ''
ms.custom: seodec18, SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML schemas [Office development in Visual Studio], mapping
- mappings [Office development in Visual Studio], XML schemas to Word documents
- Word [Office development in Visual Studio], mapping XML schemas
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 082d5fe4fbcc7f66709770c16d3c9a1a2811e60d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900931"
---
# <a name="how-to-map-schemas-to-word-documents-inside-visual-studio"></a>Comment : mapper des schémas à des documents Word dans Visual Studio
  **Important** Les informations fournies dans cette rubrique concernant Microsoft Word sont présentées exclusivement pour l’avantage et l’utilisation des personnes et des organisations situées en dehors du États-Unis et de ses territoires, ou qui utilisent ou développent des programmes qui s’exécutent sur les produits Microsoft Word qui étaient sous licence par Microsoft avant le 2010 du 1er janvier, lorsque Microsoft a supprimé une implémentation de fonctionnalités particulières liées au code XML personnalisé de Ces informations relatives à Microsoft Word peuvent ne pas être lues ou utilisées par des personnes ou des organisations du États-Unis ou de ses territoires qui utilisent ou développent des programmes qui s’exécutent sur, les produits Microsoft Word qui étaient sous licence par Microsoft après le 10 janvier 2010 ; ces produits ne se comportent pas de la même façon que les produits sous licence avant cette date ou achetés et sous licence pour une utilisation en dehors du États-Unis.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Vous pouvez mapper un schéma XML à un document lorsque le document est ouvert dans Visual Studio. Vous utilisez les mêmes outils Word Microsoft Office que ceux que vous utilisez lorsque le document est ouvert en dehors de Visual Studio. Le projet Office crée les mêmes objets si vous mappez le schéma au document avant ou après la création de votre solution Word.

## <a name="to-map-an-xml-schema-to-a-word-document-in-visual-studio"></a>Pour mapper un schéma XML à un document Word dans Visual Studio

1. Ouvrez le document Word ou le projet de modèle dans Visual Studio.

2. Cliquez dans le document pour déplacer le focus sur le concepteur.

3. Dans le ruban, cliquez sur l’onglet **développeur** .

    > [!NOTE]
    > Si l'onglet **Développeur** n'est pas visible, vous devez tout d'abord l'afficher. Pour plus d’informations, consultez [Comment : afficher l’onglet Développeur sur le ruban](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

4. Dans le groupe **XML** , cliquez sur **schéma**.

     La boîte de dialogue **modèles et compléments** s’ouvre.

5. Cliquez sur l’onglet **schéma XML** .

6. Cliquez sur **Ajouter un schéma**.

     La boîte de dialogue **Ajouter un schéma** s’ouvre.

7. Accédez à votre fichier de schéma, sélectionnez-le, puis cliquez sur **ouvrir**.

     La boîte de dialogue **paramètres de schéma** s’ouvre.

8. Affectez un alias ou cliquez sur **OK** pour ajouter le schéma sans alias.

9. Cliquez sur **OK**.

     La fenêtre **structure XML** s’ouvre.

10. Faites glisser des éléments de la fenêtre **structure XML** vers les emplacements de votre document où vous souhaitez créer les contrôles correspondants.

## <a name="see-also"></a>Voir aussi
- [Comment : mapper des schémas à des feuilles de calcul dans Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
- [Schémas et données XML dans les personnalisations au niveau du document](../vsto/xml-schemas-and-data-in-document-level-customizations.md)
