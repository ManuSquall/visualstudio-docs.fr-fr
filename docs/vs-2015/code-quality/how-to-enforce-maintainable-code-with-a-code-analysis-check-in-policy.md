---
title: 'Comment : appliquer du code facile à maintenir avec une stratégie d’archivage de l’analyse du code | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: d1b3b04f-4dd9-40e6-b2d4-b414d33fb647
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0d54ca9a31e8a1bbd2496bf8689a119e53580c79
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660216"
---
# <a name="how-to-enforce-maintainable-code-with-a-code-analysis-check-in-policy"></a>Comment : appliquer du code facile à maintenir avec une stratégie d’archivage de l’analyse du code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les développeurs peuvent utiliser l’outil de métrique du code pour mesurer la complexité et la facilité de gestion de leur code, mais ils ne peuvent pas appeler de métriques du code dans le cadre d’une stratégie d’archivage. Toutefois, une équipe peut activer des règles d’analyse du code qui vérifient la conformité de leur code avec les normes de métrique du code et applique les règles à l’aide de stratégies d’archivage. Pour plus d’informations sur les métriques du code, consultez les valeurs de la [métrique du code](../code-quality/code-metrics-values.md).

 Les développeurs peuvent activer la profondeur d’héritage, le couplage de classe, l’index de maintenabilité et les règles de complexité pour appliquer du code gérable grâce à des stratégies d’archivage de l’analyse du code. Ces quatre règles se trouvent sous la catégorie « règles de maintenabilité » dans l’éditeur de stratégie d’analyse du code.

 Les administrateurs du contrôle de version pour [!INCLUDE[esprfound](../includes/esprfound-md.md)] peuvent ajouter les règles de maintenabilité de l’analyse du code aux spécifications de la stratégie d’archivage. Ces stratégies d’archivage requièrent que les développeurs exécutent l’analyse du code en fonction de ces modifications de règles avant d’initier un archivage.

### <a name="to-open-the-code-analysis-policy-editor"></a>Pour ouvrir l’éditeur de stratégie d’analyse du code

1. Dans **Team Explorer**, cliquez avec le bouton droit sur le projet d’équipe, cliquez sur **paramètres du projet d’équipe**, puis sur contrôle de **code source**.

     La boîte de dialogue **contrôle de code source** s’affiche.

2. Sous l’onglet **stratégie d’archivage** , puis cliquez sur **Ajouter**.

     La boîte de dialogue **Ajouter une stratégie d’archivage** s’affiche.

3. Dans la liste **stratégie d’archivage** , activez la case à cocher **analyse du code** , puis cliquez sur **OK**.

     La boîte de dialogue **éditeur de stratégie d’analyse du code** s’affiche.

### <a name="to-enable-code-analysis-maintainability-rules"></a>Pour activer les règles de maintenabilité de l’analyse du code

1. Dans la boîte de dialogue **éditeur de stratégie d’analyse du code** , sous paramètres de **règle**, développez le nœud **règles de maintenabilité** .

2. Activez les cases à cocher correspondant aux règles suivantes :

    - Profondeur d’héritage : **CA1501 AvoidExcessiveInheritance** -seuil : avertissement à plus de 5 niveaux de profondeur

    - Complexité : **CA1502 AvoidExcessiveComplexity** -seuil : avertissement à plus de 25

    - Index de maintenabilité : **ca1505 AvoidUnmaintainableCode** -seuil : avertissement à moins de 20

    - Couplage de classes : **CA1506 AvoidExcessiveClassCoupling** -threshold : Warning à plus de 80 pour une classe et plus de 30 pour une méthode

    - En outre, si vous souhaitez qu’une violation de règle empêche une génération, activez la case à cocher **traiter l’avertissement comme une erreur en** regard de la description de la règle.

3. Cliquez sur **OK**. La nouvelle stratégie d’archivage s’applique désormais aux archivages ultérieurs.

## <a name="see-also"></a>Voir aussi
 [Valeurs de métriques](../code-quality/code-metrics-values.md) [du code création et utilisation de stratégies d’archivage de l’analyse du code](../code-quality/creating-and-using-code-analysis-check-in-policies.md)
