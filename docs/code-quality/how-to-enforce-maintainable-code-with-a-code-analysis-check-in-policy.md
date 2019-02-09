---
title: 'Procédure : Appliquer du code facile à maintenir avec une stratégie d’archivage d’analyse du code'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: d1b3b04f-4dd9-40e6-b2d4-b414d33fb647
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7139c952b40957a564fcd4074b1c931817dfb851
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55911220"
---
# <a name="how-to-enforce-maintainable-code-with-a-code-analysis-check-in-policy"></a>Procédure : Appliquer du code facile à maintenir avec une stratégie d’archivage de l’analyse du code

Les développeurs peuvent utiliser l’outil de métrique du Code pour mesurer la complexité et la facilité de maintenance de leur code, mais vous ne pouvez pas appeler métrique du Code dans le cadre d’une stratégie d’archivage. Toutefois, vous pouvez activer les règles d’analyse du Code qui vérifient la conformité de votre code avec les normes des métriques de code et appliquer les règles via des stratégies d’archivage. Pour plus d’informations sur la métrique du code, consultez [les valeurs de métriques de Code](../code-quality/code-metrics-values.md).

Vous pouvez activer la profondeur d’héritage, couplage de classe, indice de maintenabilité et règles de complexité appliquer du code facile à gérer via une stratégie d’archivage de l’analyse du Code. Les quatre de ces règles sont trouvent sous la catégorie « Règles de maintenance » dans l’éditeur de stratégie d’analyse du Code.

Les administrateurs du contrôle de version de Team Foundation peuvent ajouter des règles de la facilité de gestion d’analyse du Code aux exigences de stratégie d’archivage. Ces archivage stratégies obliger les développeurs à exécuter l’analyse du Code en fonction de ces modifications de règle avant de lancer un archivage.

## <a name="to-open-the-code-analysis-policy-editor"></a>Pour ouvrir l’éditeur de stratégie d’analyse du Code

1. Dans **Team Explorer**, cliquez sur le projet, cliquez sur **paramètres du projet**, puis cliquez sur **contrôle de code Source**.

     Le **contrôle de code Source** boîte de dialogue s’affiche.

2. Sur le **stratégie d’archivage** onglet, puis cliquez sur **ajouter**.

     Le **ajouter la stratégie d’archivage** boîte de dialogue s’affiche.

3. Dans le **stratégie d’archivage** liste, sélectionnez le **analyse du Code** case à cocher, puis cliquez sur **OK**.

     Le **éditeur de stratégie de Code Analysis** boîte de dialogue s’affiche.

## <a name="to-enable-code-analysis-maintainability-rules"></a>Pour activer les règles d’analyse du code la facilité de maintenance

1. Dans le **éditeur de stratégie de Code Analysis** boîte de dialogue **les paramètres de règle**, développez le **règles de maintenabilité** nœud.

2. Sélectionnez les cases à cocher pour les règles suivantes :

   - Profondeur d’héritage : **CA1501 AvoidExcessiveInheritance** -seuil : Avertissement à plus de 5 niveaux de profondeur

   - Complexité : **CA1502 AvoidExcessiveComplexity** -seuil : Avertissement à plus de 25

   - Indice de maintenabilité : **CA1505 AvoidUnmaintainableCode** -seuil : Avertissement à moins de 20

   - COUPLAGE de classe : **CA1506 AvoidExcessiveClassCoupling** -seuil : Avertissement à plus de 80 pour une classe et plus de 30 pour une méthode

     En outre, si vous souhaitez une violation de règle pour empêcher une génération réussie, sélectionnez le **traiter un avertissement comme une erreur** case à cocher en regard de la description de la règle.

3. Cliquez sur **OK**. La nouvelle stratégie de vérification s’applique désormais aux archivages ultérieurs.

## <a name="see-also"></a>Voir aussi

- [Valeurs de métriques de code](../code-quality/code-metrics-values.md)
- [Création et utilisation de stratégies d’archivage de l’analyse du code](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)