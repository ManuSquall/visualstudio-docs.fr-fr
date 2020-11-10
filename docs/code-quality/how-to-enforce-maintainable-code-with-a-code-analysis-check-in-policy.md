---
title: Utiliser une stratégie d’archivage de l’analyse du code
ms.date: 11/04/2016
description: Découvrez comment utiliser une stratégie d’archivage de l’analyse du code pour vérifier que le code est conforme à l’héritage, au couplage des classes, à la maintenabilité et aux normes de complexité.
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: d1b3b04f-4dd9-40e6-b2d4-b414d33fb647
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6fa97f52f67e08b2ccf0843e5b5400680ed1c020
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94434816"
---
# <a name="how-to-enforce-maintainable-code-with-a-code-analysis-check-in-policy"></a>Comment : appliquer du code facile à maintenir avec une stratégie d’archivage de l’analyse du code

Les développeurs peuvent utiliser l’outil de métrique du code pour mesurer la complexité et la facilité de gestion de leur code, mais vous ne pouvez pas appeler de métriques du code dans le cadre d’une stratégie d’archivage. Toutefois, vous pouvez activer des règles d’analyse du code qui vérifient la conformité de votre code avec les normes de métrique du code et appliquer les règles à l’aide de stratégies d’archivage. Pour plus d’informations sur les métriques du code, consultez valeurs de la [métrique du code](../code-quality/code-metrics-values.md).

Vous pouvez activer la profondeur d’héritage, le couplage de classe, l’index de maintenabilité et les règles de complexité pour appliquer du code gérable par le biais d’une stratégie d’archivage d’analyse du code. Ces quatre règles se trouvent sous la catégorie « règles de maintenabilité » dans l’éditeur de stratégie d’analyse du code.

Les administrateurs du contrôle de version pour Team Foundation peuvent ajouter les règles de maintenabilité de l’analyse du code aux spécifications de la stratégie d’archivage. Ces stratégies d’archivage requièrent que les développeurs exécutent l’analyse du code en fonction de ces modifications de règles avant d’initier un archivage.

## <a name="to-open-the-code-analysis-policy-editor"></a>Pour ouvrir l’éditeur de stratégie d’analyse du code

1. Dans **Team Explorer** , cliquez avec le bouton droit sur le projet, cliquez sur **paramètres du projet** , puis sur **contrôle de code source**.

     La boîte de dialogue **contrôle de code source** s’affiche.

2. Sous l’onglet **stratégie d’archivage** , puis cliquez sur **Ajouter**.

     La boîte de dialogue **Ajouter une stratégie d’archivage** s’affiche.

3. Dans la liste **stratégie d’archivage** , activez la case à cocher **analyse du code** , puis cliquez sur **OK**.

     La boîte de dialogue **éditeur de stratégie d’analyse du code** s’affiche.

## <a name="to-enable-code-analysis-maintainability-rules"></a>Pour activer les règles de maintenabilité de l’analyse du code

1. Dans la boîte de dialogue **éditeur de stratégie d’analyse du code** , sous paramètres de **règle** , développez le nœud **règles de maintenabilité** .

2. Activez les cases à cocher correspondant aux règles suivantes :

   - Profondeur d’héritage : **CA1501 AvoidExcessiveInheritance** -seuil : avertissement à plus de 5 niveaux de profondeur

   - Complexité : **CA1502 AvoidExcessiveComplexity** -seuil : avertissement à plus de 25

   - Index de maintenabilité : **ca1505 AvoidUnmaintainableCode** -seuil : avertissement à moins de 20

   - Couplage de classes : **CA1506 AvoidExcessiveClassCoupling** -threshold : Warning à plus de 80 pour une classe et plus de 30 pour une méthode

     En outre, si vous souhaitez qu’une violation de règle empêche une génération réussie, activez la case à cocher **traiter l’avertissement comme une erreur en** regard de la description de la règle.

3. Cliquez sur **OK**. La nouvelle stratégie d’archivage s’applique désormais aux archivages ultérieurs.

## <a name="see-also"></a>Voir aussi

- [Valeurs de la métrique du code](../code-quality/code-metrics-values.md)
- [Création et utilisation de stratégies d’archivage de l’analyse du code](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)
