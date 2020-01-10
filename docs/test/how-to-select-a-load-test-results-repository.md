---
title: 'Comment : sélectionner un référentiel de résultats des tests de charge'
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.dialog.connectstringmissing
- vs.test.load.dialog.databaseconnectstring
helpviewer_keywords:
- load tests, results repository
- results, load test
- load test results, repository
- Load Test Results Repository
- SQL, Load Test Results Store
ms.assetid: fa0c4dd9-612f-4a57-b8eb-458f129d9cda
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 513dd884f65e041e7ad90dda1483633fec57e100
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589004"
---
# <a name="how-to-select-a-load-test-results-repository"></a>Guide pratique pour sélectionner un référentiel de résultats des tests de charge

Vous n'êtes pas limité à un magasin de résultats local. Souvent, les tests de charge sont exécutés sur un jeu distant d'ordinateurs agents. Les agents, utilisés conjointement avec un contrôleur, peuvent générer une charge simulée plus importante qu'un ordinateur unique. Pour plus d’informations, consultez [Contrôleurs de test et agents de test](configure-test-agents-and-controllers-for-load-tests.md).

Vous pouvez enregistrer les résultats des tests de vos agents ou de votre ordinateur local sur un serveur SQL sur lequel vous avez créé un magasin de résultats de tests de charge. Dans les deux cas, vous devez identifier l’emplacement auquel stocker les résultats de votre test de charge à l’aide de la fenêtre **Administrer le contrôleur de test**.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="identify-a-results-store-for-load-test-data"></a>Identifier un magasin de résultats pour les données de test de charge

1. Dans **l’Explorateur de solutions**, ouvrez votre fichier de test de charge.

2. Dans la barre d’outils **Test de charge**, sélectionnez **Gérer les contrôleurs de test**. La boîte de dialogue **Gérer le contrôleur de test** s’affiche. Si vous utilisez un agent à distance, vous devez sélectionner un contrôleur.

     ![Propriétés de connexion du magasin des résultats du test de charge](../test/media/loadtestconnectionproperties.png) Propriétés de connexion du magasin des résultats du test de charge

3. Dans le **Magasin des résultats des tests de charge**, cliquez sur **(…)** pour afficher la boîte de dialogue **Propriétés de connexion**.

4. Dans **Nom du serveur**, tapez le nom du serveur où vous avez exécuté les scripts `LoadTest`.

    > [!TIP]
    > Si vous utilisez SQL Express sur votre ordinateur local pour le magasin de tests de charge, entrez \<nom_ordinateur>\sqlexpress (par exemple **MonOrdinateur\sqlexpress**).

5. Sous **Connexion au serveur**, vous pouvez choisir **Utiliser l’authentification Windows**. Vous pouvez spécifier le nom d’utilisateur et le mot de passe, mais dans ce cas, vous devez sélectionner l’option **Enregistrer mon mot de passe**.

6. Sous **Connexion à la base de données**, choisissez **Sélectionner ou entrer un nom de base de données**. Sélectionnez **LoadTest** dans la zone de liste déroulante.

7. Cliquez sur **OK**. Vous pouvez tester la connexion en cliquant sur **Tester la connexion**.

8. Choisissez **Fermer** dans la boîte de dialogue **Gérer le contrôleur de test**.

## <a name="see-also"></a>Voir aussi

- [Gérer des résultats des tests de charge dans le référentiel des résultats des tests de charge](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Contrôleurs de test et agents de test](configure-test-agents-and-controllers-for-load-tests.md)
