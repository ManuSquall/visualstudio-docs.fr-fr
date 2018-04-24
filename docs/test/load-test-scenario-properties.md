---
title: Propriétés du scénario de test de charge Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, properties
- load tests, scenarios
ms.assetid: 4414a638-1fa2-40ad-b1f4-b99f90b62e62
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 144a875822034ef3ae10a4f0cb5f1771ebf61fb7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="load-test-scenario-properties"></a>Propriétés du scénario de test de charge

Changez les paramètres des propriétés de votre scénario de test de charge dans Visual Studio selon vos besoins de test de charge. Cet article répertorie les différentes propriétés de scénario de test de charge par catégorie.

## <a name="general"></a>Général

|Propriété|Définition|
|--------------|----------------|
|**Name**|Nom du scénario.|

## <a name="mix"></a>Combinaison

|Propriété|Définition|
|--------------|----------------|
|**Combinaison de navigateurs**|Spécifie la combinaison de navigateurs web du test de charge. Vous pouvez spécifier différents types de navigateurs web et leur répartition de charge.<br /><br />Choisissez le bouton de sélection (...) pour ouvrir la boîte de dialogue Modifier la combinaison de navigateurs et utilisez **Ajouter** et **Supprimer** pour sélectionner les types de navigateur web dans le test de charge.<br /><br />Pour plus d’informations, consultez [Spécification de types de navigateurs web](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).|
|**Combinaison de réseaux**|Spécifie la combinaison de réseaux pour le test de charge. Vous pouvez spécifier les types de réseau à inclure et leur répartition de charge.<br /><br />Choisissez le bouton de sélection (...) pour ouvrir la boîte de dialogue **Modifier la combinaison de réseaux** et utilisez **Ajouter** et **Supprimer** pour sélectionner les types de réseau dans le test de charge.<br /><br />Pour plus d’informations, consultez [Spécification de types de réseaux virtuels](../test/specify-virtual-network-types-in-a-load-test-scenario.md).|
|**Combinaison de tests**|Spécifie la combinaison des tests de performances de site web et des tests unitaires pour le test de charge. Vous pouvez spécifier les tests à inclure et leur répartition de charge.<br /><br />Choisissez le bouton de sélection (...) pour ouvrir la boîte de dialogue **Modifier la combinaison de tests** et utilisez **Ajouter** et **Supprimer** pour sélectionner les tests dans le test de charge.<br /><br />Pour plus d’informations, consultez [Modification de la combinaison de tests pour un scénario de test de charge](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).|
|**Type de combinaison de tests**|Spécifie le modèle de combinaison de tests pour le test de charge.<br /><br />Choisissez le bouton de sélection (...) pour ouvrir la boîte de dialogue **Type de combinaison de tests** et utilisez le menu déroulant sous **Modèle de combinaison de tests** pour sélectionner le modèle de combinaison de tests à utiliser dans le test de charge.<br /><br />Pour plus d’informations, consultez [Modification des modèles de combinaison de tests](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).|

## <a name="options"></a>Options

|Propriété|Définition|
|--------------|----------------|
|**Agents à utiliser**|Spécifie les agents que votre scénario doit utiliser si vous exécutez le test de charge à distance. Par exemple, vous pouvez définir un ensemble spécifique d'agents afin de maintenir une cohérence lorsque vous analysez des tendances de performance. En outre, les agents peuvent être distribués géographiquement, afin qu'il y ait une affinité entre les scripts qu'ils exécutent et l'emplacement des agents.<br /><br />Les agents doivent être séparés par des virgules, par exemple « **Agent1, Agent2, Agent3** ». Si vous laissez la propriété vide, le scénario doit utiliser tous les agents disponibles.<br /><br />Pour plus d’informations, consultez [Guide pratique pour spécifier les agents de test à utiliser](../test/how-to-specify-test-agents-to-use-in-load-test-scenarios.md).|
|**Appliquer une distribution au rythme**|Valeur booléenne utilisée pour indiquer si vous souhaitez appliquer les délais de distribution classiques au modèle de combinaison de tests sur la base du rythme de l’utilisateur. Cette propriété s’applique uniquement si la propriété **Type de combinaison de tests** a la valeur **Sur la base du rythme de l’utilisateur**.<br /><br />Pour plus d’informations, consultez [Guide pratique pour appliquer une distribution au rythme](../test/how-to-apply-distribution-to-pacing-delay-when-using-a-user-pace-test-mix-model.md).|
|**Commutation IP**|Valeur booléenne utilisée pour indiquer si la commutation IP est utilisée.<br /><br />La commutation IP permet à un agent de test d’envoyer des demandes à un serveur à l’aide d’une plage d’adresses IP. Cela simule des appels provenant de différents ordinateurs clients. La commutation IP est importante pendant les tests de batteries de serveurs web à charge équilibrée. La plupart des équilibrages de charge établissent une affinité entre un client et un serveur web à l'aide de l'adresse IP du client. Si toutes les demandes semblent provenir d’un seul client, l’équilibrage de charge n’équilibre pas la charge. Pour obtenir le bon équilibre de charge dans la batterie de serveurs web, assurez-vous que les demandes proviennent d’une plage d’adresses IP.<br /><br />La commutation IP est uniquement disponible avec l’agent de test.|
|**Nombre maximal d’itérations de test**|Valeur numérique utilisée pour spécifier le nombre maximal de tests à exécuter dans le scénario. Une valeur de 0 indique aucune limite maximum.<br /><br />Pour plus d’informations, consultez [Configuration des itérations de test pour des scénarios](../test/configure-test-iterations-in-a-load-test-scenario.md).|
|**Pourcentage de nouveaux utilisateurs**|Valeur numérique qui indique le pourcentage de nouveaux utilisateurs ou des premières visites dans le scénario.<br /><br />Pour plus d’informations, consultez [Guide pratique pour spécifier le pourcentage des utilisateurs virtuels qui utilisent les données du cache web](../test/how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data.md).|
|**Profil de réflexion**|Indique si le scénario doit utiliser **Distribution normale**, ou si le profil de réflexion est **Actif** ou **Inactif**.<br /><br />Pour plus d’informations, consultez [Modification des temps de réflexion pour simuler les retards d’interaction humaine avec un site web](../test/edit-think-times-in-load-test-scenarios.md).|

## <a name="timing"></a>Minutage

|Propriété|Définition|
|--------------|----------------|
|**Retarder l’heure de début**|Valeur de temps indiquant le délai en nombre d'heures, de minutes et de secondes à l'issue duquel le scénario démarre après le démarrage du test de charge. Si la propriété **Désactiver pendant le préchauffage** a la valeur **True**, le délai d’attente s’applique à l’issue de la période de préparation.<br /><br />Pour plus d’informations, consultez [Configuration des délais de démarrage des scénarios](../test/configure-scenario-start-delays.md).|
|**Désactiver pendant le préchauffage**|Valeur booléenne utilisée pour indiquer si le scénario doit être exécuté conformément à la durée de la propriété **Durée de préchauffage** spécifiée dans le paramètre d’exécution du test de charge.<br /><br />Pour plus d’informations sur les propriétés des paramètres d’exécution du test de charge, consultez [Propriétés des paramètres d’exécution pour le test de charge](../test/load-test-run-settings-properties.md).<br /><br />Pour plus d’informations, consultez [Configuration des délais de démarrage des scénarios](../test/configure-scenario-start-delays.md).|
|**Temps de réflexion entre les itérations de test**|Valeur numérique utilisée pour spécifier le délai d'attente exprimé en secondes entre les itérations de test.<br /><br />Pour plus d’informations, consultez [Modification des temps de réflexion pour simuler les retards d’interaction humaine avec un site web](../test/edit-think-times-in-load-test-scenarios.md).|

## <a name="see-also"></a>Voir aussi

- [Modification des scénarios de test de charge](../test/edit-load-test-scenarios.md)