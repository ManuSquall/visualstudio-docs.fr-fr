---
title: Émulateur Express pour exécuter/déboguer le service Cloud Azure localement
ms.custom: SEO-VS-2020
description: Utilisation de l’émulateur express pour exécuter et déboguer un service cloud sur une machine locale
author: mikejo5000
manager: jillfra
ms.topic: how-to
ms.workload: azure-vs
ms.date: 03/06/2017
ms.author: mikejo
ms.openlocfilehash: dee97ab487f4e165fd372559e51b6f19c3501e9f
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94902439"
---
# <a name="using-emulator-express-to-run-and-debug-an-azure-cloud-service-on-a-local-machine"></a>Utiliser l’émulateur express pour exécuter et déboguer un service cloud Azure sur une machine locale
Avec l’émulateur express, vous testez et déboguez un service cloud sans avoir à exécuter Visual Studio en tant qu’administrateur. Vous pouvez définir les paramètres du projet pour utiliser l’émulateur express ou l’émulateur complet selon la configuration requise de votre service cloud. Pour plus d’informations sur l’émulateur complet, consultez [Exécuter une application Azure dans l’émulateur de calcul](/azure/storage/common/storage-use-emulator).

## <a name="using-emulator-express-in-visual-studio"></a>Utiliser l’émulateur express dans Visual Studio
Quand vous créez un projet Azure dans le Kit de développement logiciel (SDK) Azure 2.3 ou une version ultérieure, l’émulateur express est automatiquement utilisé. Dans le cas des projets existants créés à l’aide d’une version antérieure du Kit SDK Azure, suivez ces étapes pour sélectionner l’émulateur express :

1. Créez ou ouvrez un projet de service cloud Azure dans Visual Studio.

1. Dans Explorateur de solutions, cliquez avec le bouton droit sur le projet, puis, dans le menu contextuel, sélectionnez **Propriétés**.

1. Sur les pages de propriétés des projets, sélectionnez l’onglet **Web**.

    ![Propriétés pour un projet de service cloud Azure](./media/vs-azure-tools-emulator-express-debug-run/web-properties.png)

1. Sous **Serveur de développement local**, sélectionnez **l’option Utiliser IIS Express**.

1. Sous **Émulateur**, sélectionnez **Utiliser l’émulateur express**.

1. Pour lancer l’émulateur express, exécutez la commande suivante à l’invite de commande :

    ```
    csrun.exe /useemulatorexpress
    ```

## <a name="emulator-express-limitations"></a>Limitations de l’émulateur express
Les problèmes suivants sont des restrictions connues de l’émulateur express :

- L’émulateur express n’est pas compatible avec le serveur web IIS.
- Votre service cloud peut contenir plusieurs rôles, mais chaque rôle est limité à une seule instance.
- Vous n’avez pas accès aux numéros de port inférieurs à 1 000. Si vous faites appel à un fournisseur d’authentification qui utilise habituellement un numéro de port inférieur à 1000, vous devrez peut-être remplacer cette valeur par un numéro de port supérieur à 1000.
- Les limitations qui s’appliquent à l’émulateur de calcul Azure s’appliquent aussi à l’émulateur express. Par exemple, il ne peut pas y avoir plus de 50 instances de rôle par déploiement. Pour plus d’informations sur l’émulateur de calcul Azure, consultez la page [Exécuter une application Azure dans l’émulateur de calcul](vs-azure-tools-performance-profiling-cloud-services.md).

## <a name="next-steps"></a>Étapes suivantes
[Débogage des services Cloud Azure](vs-azure-tools-debugging-cloud-services-overview.md)
