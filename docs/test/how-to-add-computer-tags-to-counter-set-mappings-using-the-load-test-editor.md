---
title: Ajouter des étiquettes d’ordinateur aux mappages des ensembles de compteurs pour un test de charge dans Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, counter set mappings, computer tags
ms.assetid: f52a73e1-036a-4b28-a6c8-848284bf4488
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: d6b14ef4ae42ef978c449f7cb4bafaa08bf8a1a6
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31968133"
---
# <a name="how-to-add-computer-tags-to-counter-set-mappings-using-the-load-test-editor"></a>Comment : ajouter des étiquettes d’ordinateur aux mappages des ensembles de compteurs à l’aide de l’éditeur de test de charge

Les étiquettes d’ordinateur permettent d’identifier un ordinateur avec un nom facile à reconnaître. Les étiquettes s’affichent dans le nœud **Mappages des ensembles de compteurs** de l’arborescence de l’éditeur de test de charge. Plus important, les étiquettes s’affichent dans les rapports Excel, ce qui permet aux parties prenantes d’identifier le rôle de l’ordinateur dans le test de charge. Par exemple, « Server1 Web dans lab2 » ou « SQL Server2 dans le bureau de Phoenix ». Pour plus d’informations, consultez [Création de rapports sur les résultats des tests de charge pour les comparaisons de tests ou l’analyse de tendances](../test/compare-load-test-results.md).

## <a name="to-add-a-tag-to-a-computer"></a>Pour ajouter une étiquette à un ordinateur

1.  Ouvrez un test de charge.

2.  Choisissez le bouton **Gérer les ensembles de compteurs**.

     – ou –

     Cliquez avec le bouton droit sur le dossier **Ensembles de compteurs** dans l’arborescence du test de charge, puis choisissez **Gérer les ensembles de compteurs**.

     La boîte de dialogue **Gérer les ensembles de compteurs** s’affiche.

3.  (Facultatif) Dans la zone de liste **Les ordinateurs et les ensembles de compteurs sélectionnés seront ajoutés aux paramètres d’exécution par défaut**, sélectionnez un paramètre d’exécution distinct.

    > [!NOTE]
    > Cela ne s'applique que si votre test de charge comporte plusieurs paramètres d'exécution.

4.  Sous **Ordinateurs et ensembles de compteurs à surveiller**, sélectionnez l’ordinateur auquel vous souhaitez appliquer l’étiquette.

    > [!NOTE]
    > Pour plus d’informations sur l’ajout d’un ordinateur, consultez [Guide pratique pour gérer des ensembles de compteurs](../test/how-to-manage-counter-sets-using-the-load-test-editor.md).

5.  Dans la zone de texte **Étiquettes d’ordinateur**, tapez une étiquette à associer à l’ordinateur. Par exemple, « TestMachine12 dans lab3 ».

6.  Cliquez sur **OK**.

## <a name="see-also"></a>Voir aussi

- [Analyse des violations des règles de seuil](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [Analyser les résultats des tests de charge](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Spécification des ensembles de compteurs et des règles de seuil pour les ordinateurs dans un test de charge](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Guide pratique pour gérer des ensembles de compteurs](../test/how-to-manage-counter-sets-using-the-load-test-editor.md)