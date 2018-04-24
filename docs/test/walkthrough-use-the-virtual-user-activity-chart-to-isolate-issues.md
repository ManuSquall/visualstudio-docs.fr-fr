---
title: Utilisation du graphique d’activités des utilisateurs virtuels pour les tests de charge dans Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, virtual user activity chart
- virtual user activity chart, isolating performance issues
ms.assetid: d1c10fb9-cfeb-4e7f-9991-2d1e1103699e
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 7cf4d2d31bb037aba8af95caf5ffab1d7be2c132
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-using-the-virtual-user-activity-chart-to-isolate-issues"></a>Procédure pas à pas : utilisation du graphique d'activités des utilisateurs virtuels pour isoler les problèmes de performances

Dans cette procédure pas à pas, vous apprendrez à utiliser le graphique d'activités des utilisateurs virtuels pour isoler des erreurs qui se sont produites pour les utilisateurs virtuels individuels qui ont exécuté votre test de charge.

 Le graphique d'activités des utilisateurs virtuels vous permet de visualiser les activités des utilisateurs virtuels associées à votre test de charge. Chaque ligne du graphique représente un utilisateur virtuel individuel. Le graphique d'activités des utilisateurs virtuels vous montre exactement ce que chaque utilisateur virtuel faisait pendant le test. Il permet d’isoler les problèmes de performances en visualisant les modèles d’activités des utilisateurs et les modèles de charge, de mettre en corrélation des tests lents ou ayant échoué et de consulter des requêtes basées sur d’autres activités des utilisateurs virtuels. Le graphique d'activités des utilisateurs virtuels est disponible uniquement une fois l'exécution du test de charge terminée.

 Dans cette procédure pas à pas, vous effectuerez les tâches suivantes :

-   Apprenez comment utiliser les outils suivants associés au graphique d'activités des utilisateurs virtuels :

    -   Utilisez l’outil **Zoomer sur la période de temps** pour spécifier une période spécifique sur le graphique à analyser.

    -   Utilisez le volet **Légende du détail** et le volet **Résultats du filtre** pour appliquer filtrage au graphique pour isoler des problèmes.

-   Utilisez le graphique d'activités des utilisateurs virtuels pour analyser une erreur qui s'est produite pour un utilisateur virtuel spécifique et afficher les détails du type d'erreur problématique.

 Pour plus d’informations, consultez [Analyse de l’activité des utilisateurs virtuels dans la vue Détails](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).

## <a name="prerequisites"></a>Prérequis

-   Visual Studio Enterprise

-   Exécutez les procédures suivantes :

    -   [Enregistrer et exécuter un test de performances web](http://msdn.microsoft.com/en-us/bd0a82fd-cec0-4861-bc09-e1b0b2d258ef)

    -   [Créer et exécuter un test de charge](http://msdn.microsoft.com/en-us/7041cbcf-9ab1-4579-98ff-8f296aeaded4)

## <a name="open-the-colorwebapp-solution-created-in-the-previous-walkthroughs"></a>Ouvrir la solution ColorWebApp créée dans les procédures pas à pas précédentes

### <a name="open-the-solution"></a>Ouvrir la solution

1.  Démarrez Visual Studio.

2.  Ouvrez la solution ColorWebApp qui contient LoadTest1.loadtest. Ce test de charge résulte des trois procédures pas à pas répertoriées au début de cette rubrique dans la section des conditions requises.

     Les étapes restantes de cette procédure pas à pas supposent qu'ils existe une applications web nommée ColorWebApp, un test de performances de site web nommé ColorWebAppTest.webtest et un test de charge nommé LoadTest1.loadtest.

## <a name="run-the-load-test"></a>Exécuter le test de charge
 Exécutez le test de charge pour collecter les données d'activités des utilisateurs virtuels.

### <a name="run-the-load-test-to-collect-virtual-user-activity-data"></a>Exécuter le test de charge pour collecter les données d'activités des utilisateurs virtuels

-   Dans l’éditeur de test de charge, choisissez le bouton **Exécuter** dans la barre d’outils. L'exécution de LoadTest1 démarre.

## <a name="isolate-issues-in-the-virtual-user-activity-chart"></a>Isoler les problèmes dans le graphique d'activités des utilisateurs virtuels

Une fois que vous avez exécuté le test de charge et que vous avez collecté les données d'activités des utilisateurs virtuels, vous pouvez consulter ces données dans les résultats du test de charge à l'aide de la vue Détails de l'analyseur de test de charge dans le graphique d'activités des utilisateurs virtuels. En outre, vous pouvez utiliser le graphique d'activités des utilisateurs virtuels pour contribuer à isoler les problèmes de performances dans votre test de charge.

### <a name="to-use-the-virtual-user-activity-chart-in-your-load-test-results"></a>Pour utiliser le graphique d'activités des utilisateurs virtuels dans vos résultats de test de charge

1.  À l'issue de l'exécution du test de charge, la page Résumé des résultats du test de charge s'affiche dans l'analyseur de test de charge. Choisissez le bouton **Graphiques** dans la barre d’outils.

     La vue Graphiques s'affiche.

2.  Sur le graphique **Temps de réponse de la page**, cliquez avec le bouton droit sur l’une des icônes de violation de seuil et sélectionnez **Accéder au détail de l’utilisateur**.

    > [!NOTE]
    > Vous pouvez utiliser le bouton **Détails** dans la barre d’outils de l’éditeur de test de charge pour ouvrir également le graphique d’activités des utilisateurs. Toutefois, si vous utilisez l’option **Accéder au détail de l’utilisateur**, le graphique d’activités des utilisateurs virtuels applique automatiquement un zoom avant sur la partie du test sur laquelle vous avez cliqué avec le bouton droit dans le graphique.

     La vue Détails affiche le **Graphique d’activités des utilisateurs virtuels** en se concentrant sur la période au cours de laquelle des violations de seuil se sont produites.

     Sur l'axe Y, les tracés horizontaux représentent des utilisateurs virtuels individuels. L'axe X affiche la chronologie de la série de tests de charge.

3.  Dans l’outil **Zoomer sur la période de temps** sous **Graphique d’activités des utilisateurs virtuels**, ajustez les curseurs de droite et de gauche pour les rapprocher de l’icône de violation de seuil. Cela modifie l’échelle de temps dans le **Graphique d’activités des utilisateurs virtuels**.

4.  Dans la zone **Légende du détail**, cochez la case **(Surligner les erreurs)**. Notez que l'utilisateur virtuel à l'origine de la violation de seuil est mis en surbrillance.

5.  Dans le volet **Résultats du filtre**, décochez les cases **Afficher les résultats réussis** et **Erreur HTTP**, mais laissez la case **Erreur de règle de validation** cochée.

     Le **Graphique d’activités des utilisateurs virtuels** affiche uniquement les utilisateurs virtuels qui sont restés plus de 3 secondes dans la page Red.aspx, comme spécifié par le seuil de violation configure dans la procédure pas à pas précédente.

6.  Placez le pointeur de la souris au-dessus de la ligne horizontale qui représente l’utilisateur virtuel avec l’erreur de règle de validation de la violation de seuil.

7.  Une info-bulle s'affiche avec les informations suivantes :

    -   **Identifiant utilisateur**

    -   **Scénario**

    -   **Test**

    -   **Résultat**

    -   **Network**

    -   **Heure de début**

    -   **Durée**

    -   **Agent**

    -   **Journal des tests**

8.  Notez que **Journal des tests** est un lien. Choisissez le lien **Journal des tests**.

9. Le test de performances de site web ColorWebTest associé au journal s'ouvre dans l'Afficheur des résultats des tests de performances de site web. Il permet d'identifier l'endroit où les violations de seuil se sont produites.

     Vous pouvez utiliser différents paramètres dans les volets **Légende du détail** et **Résultats du filtre** pour isoler les problèmes de performances et les erreurs dans vos tests de charge. Essayez d’utiliser ces paramètres et l’outil **Zoomer sur la période de temps** pour afficher le mode de représentation des données utilisateur virtuel dans le **Graphique d’activités des utilisateurs virtuels**.

## <a name="see-also"></a>Voir aussi

- [Analyse de l’activité des utilisateurs virtuels dans la vue Détails](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)
- [Contrôleurs de test et agents de test](configure-test-agents-and-controllers-for-load-tests.md)
- [Guide pratique pour créer un paramètre de test pour un test de charge distribué](../test/how-to-create-a-test-setting-for-a-distributed-load-test.md)
- [Installer et configurer des agents de test](../test/lab-management/install-configure-test-agents.md)
- [Collecter des informations de diagnostic à l’aide des paramètres de test](../test/collect-diagnostic-information-using-test-settings.md)