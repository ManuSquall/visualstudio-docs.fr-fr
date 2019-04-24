---
title: 'Procédure : Appliquer du Code facile à maintenir avec une stratégie d’archivage de l’analyse du Code | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: d1b3b04f-4dd9-40e6-b2d4-b414d33fb647
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 27593a450f7c2a1b34c1c84bc1d4e7ea5bb5919f
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60091874"
---
# <a name="how-to-enforce-maintainable-code-with-a-code-analysis-check-in-policy"></a>Procédure : Appliquer du code facile à maintenir avec une stratégie d’archivage d’analyse du code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les développeurs peuvent utiliser l’outil de métrique du Code pour mesurer la complexité et la facilité de maintenance de leur code, mais ils ne peuvent pas appeler métrique du code dans le cadre d’une stratégie d’archivage. Toutefois, une équipe peut activer des règles d’analyse du Code pour vérifier la conformité de leur code avec les normes de la métrique du Code et appliquent les règles via des stratégies d’archivage. Pour plus d’informations sur la métrique du code, consultez le [des valeurs de métriques de Code](../code-quality/code-metrics-values.md).  
  
 Les développeurs peuvent activer la profondeur d’héritage, couplage de classe, indice de maintenabilité et règles de complexité appliquer du code facile à gérer via des stratégies d’archivage d’analyse du Code. Les quatre de ces règles sont trouvent sous la catégorie « Règles de maintenance » dans l’éditeur de stratégie d’analyse du Code.  
  
 Les administrateurs de version contrôler pour [!INCLUDE[esprfound](../includes/esprfound-md.md)] pouvez ajouter des règles de la facilité de gestion d’analyse du Code aux exigences de stratégie d’archivage. Ces archivage stratégies obliger les développeurs à exécuter l’analyse du Code en fonction de ces modifications de règle avant de lancer un archivage.  
  
### <a name="to-open-the-code-analysis-policy-editor"></a>Pour ouvrir l’éditeur de stratégie de Code Analysis  
  
1. Dans **Team Explorer**, cliquez sur le projet d’équipe, cliquez sur **paramètres du projet d’équipe**, puis cliquez sur **contrôle de code Source**.  
  
     Le **contrôle de code Source** boîte de dialogue s’affiche.  
  
2. Sur le **stratégie d’archivage** onglet, puis cliquez sur **ajouter**.  
  
     Le **ajouter la stratégie d’archivage** boîte de dialogue s’affiche.  
  
3. Dans le **stratégie d’archivage** liste, sélectionnez le **analyse du Code** case à cocher, puis cliquez sur **OK**.  
  
     Le **éditeur de stratégie de Code Analysis** boîte de dialogue s’affiche.  
  
### <a name="to-enable-code-analysis-maintainability-rules"></a>Pour activer les règles d’analyse du Code la facilité de maintenance  
  
1. Dans le **éditeur de stratégie de Code Analysis** boîte de dialogue **les paramètres de règle**, développez le **règles de maintenabilité** nœud.  
  
2. Sélectionnez les cases à cocher pour les règles suivantes :  
  
    - Profondeur d’héritage : **CA1501 AvoidExcessiveInheritance** -seuil : Avertissement à plus de 5 niveaux de profondeur  
  
    - Complexité : **CA1502 AvoidExcessiveComplexity** -seuil : Avertissement à plus de 25  
  
    - Indice de maintenabilité : **CA1505 AvoidUnmaintainableCode** -seuil : Avertissement à moins de 20  
  
    - COUPLAGE de classe : **CA1506 AvoidExcessiveClassCoupling** -seuil : Avertissement à plus de 80 pour une classe et plus de 30 pour une méthode  
  
    - En outre, si vous souhaitez une violation de règle empêche une génération, sélectionnez le **traiter un avertissement comme une erreur** case à cocher en regard de la description de la règle.  
  
3. Cliquez sur **OK**. La nouvelle stratégie de vérification s’applique désormais aux archivages ultérieurs.  
  
## <a name="see-also"></a>Voir aussi  
 [Valeurs de métriques de code](../code-quality/code-metrics-values.md)   
 [Création et utilisation de stratégies d’archivage de l’analyse du code](../code-quality/creating-and-using-code-analysis-check-in-policies.md)
