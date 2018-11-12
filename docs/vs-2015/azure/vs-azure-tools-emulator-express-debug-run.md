---
title: Utiliser l’émulateur Express pour exécuter et déboguer un service cloud Azure sur un ordinateur local | Microsoft Docs
description: Utiliser l’émulateur Express pour exécuter et déboguer un service cloud sur un ordinateur local
author: mikejo5000
manager: douge
ms.assetid: 73108f98-a552-4817-b7a1-551367b71906
ms.topic: conceptual
ms.workload: azure-vs
ms.date: 03/06/2017
ms.author: mikejo
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.openlocfilehash: 28dd59e3d691df0199afffe93d68d60668c6afe4
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2018
ms.locfileid: "51001705"
---
# <a name="using-emulator-express-to-run-and-debug-an-azure-cloud-service-on-a-local-machine"></a>Utilisation de l’émulateur express pour exécuter et déboguer un service cloud Azure sur une machine locale
À l’aide de l’émulateur Express, vous pouvez tester et déboguer un service cloud sans exécuter Visual Studio en tant qu’administrateur. Vous pouvez définir les paramètres de votre projet à utiliser l’émulateur Express ou l’émulateur complet, selon les besoins de votre service cloud. Pour plus d’informations sur l’émulateur complet, consultez [exécuter une Application Azure dans l’émulateur de calcul](/azure/storage/common/storage-use-emulator).

## <a name="using-emulator-express-in-visual-studio"></a>À l’aide de l’émulateur Express dans Visual Studio
Lorsque vous créez un projet Azure dans Azure SDK 2.3 ou version ultérieure, l’émulateur Express est utilisé automatiquement. Pour les projets existants qui ont été créés avec une version antérieure du SDK Azure, procédez comme suit pour sélectionner l’émulateur Express :

1. Créez ou ouvrez un projet de service cloud Azure dans Visual Studio.

1. Dans **l’Explorateur de solutions**, cliquez sur le projet, puis, dans le menu contextuel, sélectionnez **propriétés**.

1. Dans les pages de propriétés de projets, sélectionnez le **Web** onglet.

    ![Propriétés d’un projet de service cloud Azure](./media/vs-azure-tools-emulator-express-debug-run/web-properties.png)

1. Sous **serveur de développement Local**, sélectionnez **option utiliser IIS Express**.

1. Sous **émulateur**, sélectionnez **utiliser l’émulateur Express**.
   
1. Pour lancer l’émulateur Express, exécutez la commande suivante à une invite de commandes : 

    ```
    csrun.exe /useemulatorexpress
    ```

## <a name="emulator-express-limitations"></a>Limitations d’émulateur Express
Limitations de l’émulateur Express sont connues pour les problèmes suivants : 

- L’émulateur Express n’est pas compatible avec le serveur Web IIS.
- Votre service cloud peut contenir plusieurs rôles, mais chaque rôle est limité à une instance.
- Vous ne pouvez pas accéder à des numéros de port inférieur à 1000. Si vous utilisez un fournisseur d’authentification qui utilise habituellement un port inférieur à 1000, vous devrez peut-être modifier cette valeur à un numéro de port supérieur à 1000.
- Les limitations qui s’appliquent à l’émulateur de calcul Azure s’appliquent également à l’émulateur Express. Par exemple, vous ne peut pas avoir plus de 50 instances de rôle par déploiement. Pour plus d’informations sur l’émulateur de calcul Azure, consultez [exécuter une Application Azure dans l’émulateur de calcul](http://go.microsoft.com/fwlink/p/?LinkId=623050).

## <a name="next-steps"></a>Étapes suivantes
[Débogage des services cloud Azure](https://msdn.microsoft.com/library/azure/ee405479.aspx)
