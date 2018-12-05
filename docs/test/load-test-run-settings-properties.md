---
title: Paramètres d'exécution du test de charge
ms.date: 10/19/2016
ms.topic: reference
helpviewer_keywords:
- load tests, run settings
ms.assetid: de10dabb-02ed-403b-9e6f-0b735524988c
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 9b0123ba4e6f9565cc31f63a23bb0be0b5bee344
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2018
ms.locfileid: "52895494"
---
# <a name="load-test-run-settings-properties"></a>Propriétés des paramètres d’exécution des tests de charge

Les paramètres d’exécution d’un test de charge déterminent divers autres paramètres, y compris la durée du test, le niveau de détail de collection des résultats et les ensembles de compteurs collectés lors de l’exécution du test. Vous pouvez créer et stocker plusieurs paramètres d'exécution pour chaque test de charge, puis sélectionner un paramètre particulier à utiliser lors de l'exécution du test. Un paramètre d'exécution initial est ajouté à votre test de charge lorsque vous créez ce dernier à l'aide de l'**Assistant Nouveau test de charge**.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Les tableaux suivants décrivent les différentes propriétés des paramètres d'exécution du test de charge. Vous pouvez modifier ces propriétés pour répondre aux exigences des test de charge spécifiques.

Pour plus d’informations, consultez [Configurer les paramètres d’exécution des tests de charge](../test/configure-load-test-run-settings.md).

## <a name="general-properties"></a>Propriétés générales

|Property|Définition|
|-|----------------|
|**Description**|Description des paramètres d'exécution.|
|**Erreur maximale par type**|Le nombre maximum d'erreurs par type à enregistrer pour le test de charge.<br /><br /> Vous pouvez augmenter ce nombre si nécessaire, mais cela augmentera également la taille et le temps de traitement du résultat de test de charge.|
|**Nombre maximal d’URL de la requête pouvant faire l’objet d’un rapport**|Nombre maximal d'URL de la requête de test de performances web uniques où signaler des résultats dans ce test de charge.<br /><br /> Vous pouvez augmenter ce nombre si nécessaire, mais cela augmentera également la taille et le temps de traitement du résultat de test de charge.|
|**Nombre maximal de violations de seuils**|Le nombre maximum de violations de seuil à enregistrer pour ce test de charge.<br /><br /> Vous pouvez augmenter ce nombre si nécessaire, mais cela augmentera également la taille et le temps de traitement du résultat de test de charge.|
|**Exécuter des tests unitaires dans le domaine d’application**|Valeur booléenne déterminant si chaque assembly de test unitaire s'exécute dans un domaine d'application séparé lorsque le test de charge contient des tests unitaires. Le paramètre par défaut est True.<br /><br /> Si vos tests unitaires ne requièrent pas un fichier app.config ou un domaine d'application distinct pour fonctionner correctement, vos tests unitaires peuvent s'exécuter plus vite si cette propriété a la valeur `False`.|
|**Name**|Nom du paramètre d’exécution tel qu’il apparaît dans le nœud **Paramètres d’exécution** de **l’éditeur de test de charge**.|
|**Niveau de validation**|Définit le niveau le plus élevé de règle de validation qui s’exécutera dans un test de charge. Les règles de validation sont associées aux requêtes de tests de performances web. Chaque règle de validation a un niveau de validation associé : **Haut**, **Moyen** ou **Bas**. Ce paramètre de série de tests de charge spécifie les règles de validation qui s’exécuteront pendant que le test de performances web est exécuté dans le test de charge. Par exemple, si ce paramètre d’exécution a la valeur **Moyen**, toutes les règles de validation marquées avec la valeur **Moyen** ou **Bas** sont exécutées.|

## <a name="logging-properties"></a>Propriétés de journalisation

|Property|Définition|
|-|----------------|
|**Nombre maximal de journaux des tests**|Indique le nombre maximum de journaux des tests à enregistrer pour le test de charge. Lorsque la valeur entrée pour le nombre maximum de journaux des tests est atteint, le test de charge arrête de collecter les journaux. Par conséquent, les journaux seront collectés au début du test, non à la fin. Le test de charge continue de fonctionner jusqu'à ce qu'il soit terminé.|
|**Enregistrer la fréquence d’entrée au journal pour les tests terminés**|Spécifie la fréquence d'écriture du journal des tests. Cette valeur indique qu'un test sur le nombre de tests entré doit être enregistré dans le journal des tests. Par exemple, si vous entrez la valeur dix, cela indique que le dixième test, le vingtième test, le trentième test, et ainsi de suite, doivent être écrits dans le journal des tests. La valeur 0 indique qu'aucun journal des tests ne sera enregistré.|
|**Enregistrer le journal lors de l’échec d’un test**|Une valeur booléenne qui détermine si les journaux des tests sont enregistrés en cas d'échec d'un test dans un test de charge. La valeur par défaut est `True`.<br /><br /> Pour plus d’informations, consultez [Guide pratique pour spécifier si les échecs de test sont enregistrés dans les journaux des tests](../test/how-to-specify-if-test-failures-are-saved-to-test-logs.md).|

 Pour plus d’informations, consultez [Modifier les paramètres de journalisation des tests de charge](../test/modify-load-test-logging-settings.md).

## <a name="results-properties"></a>Propriétés des résultats

|Property|Définition|
|-|----------------|
|**Type de stockage**|Mode de stockage des compteurs de performance obtenus dans un test de charge. Les options sont les suivantes :<br /><br /> -   **Base de données** : nécessite une base de données SQL avec un **magasin des résultats des tests de charge**.<br />-   **Aucune**.|
|**Stockage des détails de minuterie**|Utilisé pour déterminer les détails qui seront stockés dans le **magasin des résultats des tests de charge**. Trois valeurs sont disponibles :<br /><br /> -   **AllIndividualDetails** : Collecter et stocker des valeurs de minuterie pour chaque test, transaction et page exécutée (ou publiée) durant le test de charge dans le **magasin des résultats des tests de charge**. C'est obligatoire si vous prévoyez d'utiliser le **graphique d'activités des utilisateurs virtuels** dans l'**analyseur de test de charge**.<br />     Pour plus d’informations, voir [Analyser l’activité des utilisateurs virtuels dans la vue Détails](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).<br />-   **Aucune** : Ne collecter aucune valeur de minuterie. Il s’agit de la valeur par défaut pour Visual Studio 2013 Update 4 et ses mises en production ultérieures.<br />-   **StatisticsOnly** : Collecter et stocker uniquement les statistiques au lieu de stocker les valeurs de minuterie pour chaque test, transaction et page exécutée (ou publiée) durant le test de charge dans le **magasin des résultats des tests de charge**.<br /><br /> Pour plus d’informations, voir [Guide pratique : Spécifier la propriété de stockage des détails de minutage](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md).|

## <a name="sql-tracing-properties"></a>Propriétés de traçage SQL

|Property|Définition|
|-|----------------|
|**Durée minimale des opérations SQL tracées**|Durée minimale d'une opération SQL à capturer par la trace SQL, en millisecondes. Par exemple, cela vous permet d'ignorer des opérations qui s'achèvent rapidement si vous essayez de trouver des opérations SQL qui sont lentes sous charge.|
|**Chaîne de connexion de traçage SQL**|Chaîne de connexion utilisée pour accéder à la base de données à tracer.|
|**Répertoire de traçage SQL**|Emplacement où le fichier de trace SQL est placé une fois la trace terminée. Ce répertoire doit avoir des autorisations d’écriture pour SQL Server et des autorisations de lecture pour le contrôleur.|
|**Traçage SQL activé**|Active le traçage des opérations SQL. La valeur par défaut est `False`.|

## <a name="test-iterations-properties"></a>Propriétés des itérations de tests

|Property|Définition|
|-|----------------|
|**Itérations de tests**|Spécifie le nombre total de tests individuels à exécuter avant que le test de charge ne soit complet. Cette propriété s'applique seulement lorsque la propriété "Utiliser les itérations de test" a la valeur `True`.|
|**Utiliser les itérations des tests**|Si le paramètre Utiliser les itérations de test a la valeur `True`, le test de charge s'exécute jusqu'à ce que les tests individuels effectués dans le test de charge atteignent le nombre spécifié par la propriété « Itérations de test ». Dans ce cas, les paramètres basés sur le temps, à savoir Durée de préchauffage, Durée d'exécution et Durée de refroidissement, sont ignorés. Si la paramètre Utiliser les itérations de test a la valeur `False`, tous les paramètres de minutage s'appliquent et le paramètre Itérations de Test est ignoré.|

 Pour plus d’informations, consultez [Guide pratique pour spécifier le nombre d’itérations de tests dans un paramètre d’exécution](../test/how-to-specify-the-number-of-test-iterations-in-a-load-test.md).

## <a name="timing-properties"></a>Propriétés de minutage

|Property|Définition|
|-|----------------|
|**Durée de refroidissement**|Durée de la période de refroidissement du test, exprimée au format hh:mm:ss. Les tests individuels d'un test de charge peuvent continuer à s'exécuter lorsque le test de charge se termine. Durant la période de refroidissement, ces tests peuvent continuer jusqu'à être terminés ou jusqu'à la fin de la période de refroidissement. Par défaut, il n'y a pas de période de refroidissement et les tests individuels sont terminés lorsque le test de charge se termine selon le paramètre Durée d'exécution.|
|**Durée d’exécution**|Longueur du test, au format hh:mm:ss.|
|**Taux d’échantillonnage**|Intervalle auquel capturer des valeurs de compteur de performance, au format hh:mm:ss.<br /><br /> Pour plus d’informations, voir [Guide pratique : Spécifier l’échantillonnage](../test/how-to-specify-the-sample-rate-for-a-load-test.md).|
|**Durée de préchauffage**|Période entre le début du test et le moment où les échantillons de données commencent à être enregistrés, au format hh:mm:ss. Fréquemment utilisé pour charger pas à pas des utilisateurs virtuels de façon à atteindre un certain niveau de charge avant d'enregistrer des valeurs d'échantillonnage. Les valeurs d’échantillonnage capturées avant la période de préchauffage sont affichées dans **l’analyseur de test de charge**.|

## <a name="webtest-connections-properties"></a>Propriétés de connexions WebTest

|Property|Définition|
|-|----------------|
|**Modèle de connexion WebTest**|Contrôle l’utilisation des connexions de l’agent de test de charge vers le serveur web pour les tests de performances web exécutés dans un test de charge. Trois options de modèle de connexion de test de performances web sont disponibles :<br /><br /> - Le modèle **Connexion par utilisateur** simule le comportement d’un utilisateur qui utilise un vrai navigateur. Lorsque le navigateur Internet Explorer 6 ou Internet Explorer 7 est simulé, chaque utilisateur virtuel qui exécute un test de performances web utilise une ou deux connexions dédiées au serveur web. La première connexion est établie lorsque la première requête du test de performances web est émise. Une deuxième connexion peut être utilisée lorsqu'une page contient plusieurs demandes dépendantes. Ces requêtes sont émises en parallèle à l'aide des deux connexions. Ces connexions sont réutilisées pour les requêtes suivantes dans le test de performances web. Les connexions sont fermées lorsque le test de performances web se termine. Un inconvénient de ce modèle est que le nombre de connexions qui est maintenu ouvert sur l'ordinateur agent peut être supérieur (jusqu'à deux fois la charge utilisateur). Par conséquent, les ressources requises pour prendre en charge ce nombre élevé de connexions peuvent limiter la charge utilisateur qui peut être pilotée à partir d'un agent de test de charge unique. Lorsque le navigateur Internet Explorer 8 est simulé, six connexions simultanées sont prises en charge.<br />- Le modèle **Pool de connexions** conserve les ressources sur l’agent de test de charge en répartissant les connexions au serveur web parmi plusieurs utilisateurs de test de performances web virtuels. Si la charge d'utilisateur est plus grande que la taille du pool de connexions, les tests de performances web exécutés par différents utilisateurs virtuels partagent une connexion. Cela signifie qu'un test de performances de site web peut devoir attendre avant d'émettre une requête lorsqu'un autre test de performances web utilise la connexion. La durée moyenne pendant laquelle un test de performances web attend avant d'envoyer une requête est suivie par le compteur de performance de test de charge "Durée d'attente moyenne d'une connexion". Ce nombre doit être inférieur au temps de réponse moyen d'une page. Si ce n'est pas le cas, la taille du pool de connexions est sans doute trop petite.<br />- Le modèle **Connexion par itération de test** spécifie l’utilisation de connexions dédiées pour chaque itération de test.|
|**Taille du pool de connexions WebTest**|Spécifie le nombre maximal de connexions à établir entre l’agent de test de charge et le serveur web. Cela s’applique uniquement au modèle **Pool de connexions**.|

##  <a name="change-run-setting-properties"></a>Changer les propriétés des paramètres d’exécution
 Vous pouvez ajouter davantage de paramètres d'exécution à votre test de charge avec divers paramètres de propriété afin de pouvoir exécuter le test de charge dans différentes conditions, par exemple, vous pouvez ajouter un nouveau paramètre de test et utiliser un taux d'échantillonnage distinct, ou vous pouvez spécifier une plus longue durée d'exécution. Vous ne pouvez utiliser qu'un seul paramètre d'exécution à la fois et vous devez spécifier le paramètre d'exécution à utiliser en le marquant comme actif. Pour obtenir un exemple, consultez [Guide pratique pour sélectionner le paramètre d’exécution actif d’un test de charge](../test/how-to-select-the-active-run-setting-for-a-load-test.md).

### <a name="to-change-run-settings"></a>Pour modifier les paramètres d'exécution

1.  Ouvrez un test de charge.

2.  Développez le dossier **Paramètres d’exécution**.

3.  Choisissez un nœud **Paramètres d’exécution**.

4.  Dans le menu **Affichage**, choisissez **Fenêtre Propriétés**.

     La **Fenêtre Propriétés** s’affiche ainsi que les propriétés du paramètre d’exécution sélectionné.

5.  Utilisez la **Fenêtre Propriétés** pour changer les paramètres d’exécution. Par exemple, remplacez la durée d’exécution par **00:05:00** pour exécuter votre test pendant cinq minutes.

    > [!NOTE]
    > Pour obtenir une liste complète des propriétés de paramètres d’exécution et leurs descriptions, consultez [Propriétés des paramètres d’exécution pour le test de charge](../test/load-test-run-settings-properties.md).

6.  Lorsque vous terminez les modifications des propriétés, enregistrez votre test de charge. Dans le menu **Fichier**, choisissez **Enregistrer**.

> [!NOTE]
> Les mappages des ensembles de compteurs font également partie des paramètres d'exécution. Pour plus d’informations, consultez [Spécifier les ensembles de compteurs et des règles de seuil pour les ordinateurs dans un test de charge](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

## <a name="see-also"></a>Voir aussi

- [Configurer les paramètres d’exécution des tests de charge](../test/configure-load-test-run-settings.md)