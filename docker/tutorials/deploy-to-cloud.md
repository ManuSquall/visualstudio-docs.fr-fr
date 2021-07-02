---
title: 'Didacticiel de l’ancrage-partie 9 : déployer dans le Cloud'
description: Déployez une application dockr sur un service Cloud pour l’hébergement.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: da38b7482396b0bf46f5566c0c4a5416c94e83eb
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222823"
---
# <a name="deploy-to-the-cloud"></a>Déployer dans le cloud

Maintenant que vous avez exécuté votre application localement, vous pouvez commencer à envisager de l’exécuter dans le Cloud afin que d’autres personnes puissent y accéder et l’utiliser. Pour ce faire, vous allez utiliser des contextes d’ancrage. Un contexte est l’endroit où vous utilisez actuellement des conteneurs. Pour le moment, vous n’avez que votre contexte « par défaut ». vous devez donc ajouter un Cloud et y déployer votre application.

## <a name="create-your-cloud-context"></a>Créer votre contexte Cloud

1. Pour commencer, vous pouvez voir les contextes que vous avez en consultant la section contextes du panneau de l’Ancreur :

   ![Affiche uniquement le contexte par défaut](media/defaultcontext.png)

Vous ne devriez voir que le contexte par défaut pour le travail local.

1. Pour effectuer un déploiement dans le Cloud, vous devez créer un nouveau contexte ACI, mais pour ce faire, vous avez d’abord besoin de l’extension de compte Azure pour vous authentifier auprès d’Azure.

   ![Ajout d’une extension Azure](media/addazureextension.png)

Vous devez configurer un compte Azure si vous n’en avez pas déjà un.

1. Vous pouvez maintenant créer votre nouveau contexte ACI. Pour ce faire, cliquez sur le bouton plus dans la section **contextes** de la vue de l’ancrage.

   ![Création de votre contexte ACI](media/createnewcontext.png)

Vous êtes alors invité à choisir le groupe de ressources sous lequel vous souhaitez exécuter ces conteneurs. Sélectionnez un groupe existant à l’aide des touches de direction ou utilisez l’option par défaut pour utiliser le nouveau groupe.

![Sélection de votre groupe de ressources](media/selectresourcegroup.png)

Vous pouvez maintenant voir votre contexte ACI dans la liste et cliquer dessus avec le bouton droit pour en faire votre contexte d’utilisation actuel :

![Vous pouvez sélectionner un nouveau contexte ACI](media/listofcontexts.png)

## <a name="run-containers-in-the-cloud"></a>Exécuter des conteneurs dans le Cloud

1. À présent, utilisez votre contexte ACI et exécutez le conteneur.

   ```bash
   docker context use myacicontext
   docker run  -dp 3000:3000 <username>/getting-started
   ```

1. Une fois l’exécution terminée, examinez le conteneur dans votre contexte.

   ![Conteneur en cours d’exécution dans votre contexte ACI](media/contextcontainer.png)

1. Pour vérifier que cela fonctionne correctement, vous pouvez cliquer avec le bouton droit sur le conteneur en cours d’exécution et choisir **afficher dans le navigateur**.

   ![Conteneur dans ACI avec adresse IP publique](media/containerinaci.png)

Et, vous pouvez voir que le conteneur s’exécute dans une adresse IP publique et fonctionne correctement !

1. Maintenant, vous pouvez consulter notre conteneur en cours d’exécution pour voir comment il fonctionne. Vous pouvez commencer par examiner les journaux de conteneur :
 
 ```bash
   docker logs distracted-jackson
   ```

1. Vous pouvez également exécuter un fichier d’exécution dans votre conteneur comme vous le feriez avec un conteneur local.
 
 ```bash
   docker exec -it distracted-jackson sh
   ```

1. Enfin, pour nettoyer votre espace de travail et vous assurer que vous n’êtes pas facturé pour continuer à exécuter le conteneur de test, vous pouvez simplement cliquer avec le bouton droit sur le conteneur en cours d’exécution et choisir **supprimer**.

## <a name="recap"></a>Récapitulatif

Fantastique, vous avez maintenant pris votre charge de travail et vous l’avez déployée correctement dans le Cloud pour la première fois. Vous pouvez effectuer tout cela à partir de la ligne de commande, ainsi que de votre contexte ACI à l’aide de `docker run` , et en utilisant également `docker compose up` pour exécuter vos applications à plusieurs conteneurs. Pour en savoir plus sur l’exécution de vos conteneurs dans le Cloud, consultez la [documentation étendue sur l’utilisation d’ACI](https://docs.docker.com/engine/context/aci-integration/).

## <a name="next-steps"></a>Étapes suivantes

Poursuivez avec le didacticiel.

> [!div class="nextstepaction"]
> [Étapes suivantes](whats-next.md)
