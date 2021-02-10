---
title: 'Test de charge : définir le pourcentage d’utilisateur virtuel à l’aide des données du cache Web'
description: Découvrez comment spécifier la propriété pourcentage de nouveaux utilisateurs dans le Fenêtre Propriétés. Vous modifiez des propriétés du scénario de test de charge dans l'éditeur de test de charge.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, virtual users
ms.assetid: f66d5d43-4121-4487-b27f-d0a0baaf7601
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: bd7c23218fca3a501aa0c56684a4fea98d304252
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943768"
---
# <a name="how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data"></a>Guide pratique pour spécifier le pourcentage des utilisateurs virtuels qui utilisent les données du cache web

Après avoir créé votre test de charge avec **l’Assistant Nouveau test de charge**, vous pouvez modifier les propriétés des scénarios en fonction de vos besoins et de vos objectifs de test avec **l’Éditeur de test de charge**. Pour obtenir une liste complète des propriétés des scénarios de test de charge et leurs descriptions, consultez [Propriétés du scénario de test de charge](../test/load-test-scenario-properties.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

La propriété **pourcentage de nouveaux utilisateurs** est définie dans la fenêtre **Propriétés** . Vous modifiez des propriétés du scénario de test de charge dans **l’Éditeur de test de charge**.

La propriété **pourcentage de nouveaux utilisateurs** affecte la façon dont le test de charge simule la mise en cache qui serait exécutée par un navigateur Web. Par défaut, la propriété **Pourcentage de nouveaux utilisateurs** est définie sur 0 %. Si la valeur de la propriété **Pourcentage de nouveaux utilisateurs** est définie sur 100 %, chaque test de performances web exécuté dans un test de charge est traité comme un utilisateur accédant au site web pour la première fois et qui n’a aucun contenu du site web dans le cache de son navigateur provenant de visites antérieures. Par conséquent, toutes les requêtes dans le test web, y compris toutes les requêtes dépendantes telles que les images, sont téléchargées.

> [!NOTE]
> Lorsque la même ressource pouvant être mise en cache est demandée plus d'une fois dans un test web, les requêtes ne sont pas téléchargées.

Si vous exécutez un test de charge sur un site web présentant un nombre significatif d’utilisateurs ayant déjà accédé au site et disposant donc probablement d’images et d’autre contenu pouvant être mis en cache localement, un paramètre défini sur 100 % pour la propriété **Pourcentage de nouveaux utilisateurs** génère plus de demandes de téléchargement que dans une utilisation réelle. Dans ce cas, vous devez estimer le pourcentage de visites sur votre site web correspondant aux utilisateurs accédant pour la première fois au site web et définir la propriété **Pourcentage de nouveaux utilisateurs** en conséquence.

## <a name="to-specify-the-percentage-of-new-users-for-a-scenario"></a>Pour spécifier le pourcentage de nouveaux utilisateurs pour un scénario

1. Ouvrez un test de charge.

     **L’éditeur de test de charge** s’affiche. L'arborescence du test de charge s'affiche.

2. Dans le dossier **Scénarios** des arborescences du test de charge, choisissez le nœud de scénario pour lequel vous voulez modifier le pourcentage de nouveaux utilisateurs.

3. Dans le menu **Affichage**, sélectionnez **Fenêtre Propriétés**.

     Les catégories et les propriétés du scénario sont affichées dans la fenêtre **Propriétés**.

4. Définissez la valeur de la propriété **pourcentage de nouveaux utilisateurs** en entrant un nombre pour le pourcentage de nouveaux utilisateurs.

5. Après avoir changé la propriété, choisissez **Enregistrer** dans le menu **Fichier**. Vous pouvez ensuite exécuter votre test de charge à l’aide de la nouvelle valeur **pourcentage de nouveaux utilisateurs** .

## <a name="see-also"></a>Voir aussi

- [Modifier les scénarios de test de charge](../test/edit-load-test-scenarios.md)
- [Procédure pas à pas : Créer et exécuter un test de charge](../test/walkthrough-create-and-run-a-load-test.md)
- [Contrôleurs de test et agents de test](configure-test-agents-and-controllers-for-load-tests.md)
- [Propriétés des scénarios de test de charge](../test/load-test-scenario-properties.md)
- [Modifier les modèles de charge pour modéliser les activités des utilisateurs virtuels](../test/edit-load-patterns-to-model-virtual-user-activities.md)
