---
title: Un rapport publié de débogage Azure cloud service avec Visual Studio et IntelliTrace | Microsoft Docs
description: Découvrez comment déboguer un service cloud avec Visual Studio et IntelliTrace
author: mikejo5000
manager: douge
ms.assetid: 5e6662fc-b917-43ea-bf2b-4f2fc3d213dc
ms.topic: conceptual
ms.custom: vs-azure
ms.workload: azure-vs
ms.date: 03/21/2017
ms.author: mikejo
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.openlocfilehash: 865642bb7c8e41f81ff4b44ce628082e19b63a56
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002012"
---
# <a name="debugging-a-published-azure-cloud-service-with-visual-studio-and-intellitrace"></a>Débogage d’un service cloud Azure publié avec Visual Studio et IntelliTrace
Grâce à IntelliTrace, vous pouvez consigner des informations de débogage détaillées pour une instance de rôle lorsqu’il s’exécute dans Azure. Si vous avez besoin rechercher la cause d’un problème, vous pouvez utiliser les journaux IntelliTrace pour parcourir votre code à partir de Visual Studio comme si elle s’exécutait dans Azure. En effet, IntelliTrace enregistre les principales données d’environnement et de l’exécution de code lorsque votre application Windows Azure s’exécute comme un service cloud dans Azure et vous permet de relire les données enregistrées à partir de Visual Studio. 

Vous pouvez utiliser IntelliTrace si Visual Studio Enterprise est installé et votre application Azure cible .NET Framework 4 ou une version ultérieure. IntelliTrace collecte des informations pour vos rôles Azure. Les machines virtuelles pour ces rôles s’exécutées toujours des systèmes d’exploitation 64 bits.

Comme alternative, vous pouvez utiliser [le débogage à distance](http://go.microsoft.com/fwlink/p/?LinkId=623041) d’attacher directement à un service cloud qui s’exécute dans Azure.

> [!IMPORTANT]
> IntelliTrace est destiné aux scénarios de débogage uniquement et ne doit pas être utilisé pour un déploiement de production.
> 

## <a name="configure-an-azure-application-for-intellitrace"></a>Configurer une application Windows Azure pour IntelliTrace
Pour activer IntelliTrace pour une application Azure, vous devez créer et publier l’application à partir d’un projet Azure Visual Studio. Vous devez configurer IntelliTrace pour votre application Azure avant de le publier sur Azure. Si vous publiez votre application sans configurer IntelliTrace, vous devez republier le projet. Pour plus d’informations, consultez [un cloud Azure de la publication de projets à l’aide de Visual Studio services](http://go.microsoft.com/fwlink/p/?LinkId=623012).

1. Lorsque vous êtes prêt à déployer votre application Windows Azure, vérifiez que vos cibles de génération de projet sont définis sur **déboguer**.

1. Dans **l’Explorateur de solutions**, avec le bouton droit de projet et, dans le menu contextuel, sélectionnez **publier**.
   
1. Dans le **publier l’Application Azure** boîte de dialogue, sélectionnez l’abonnement Azure, puis sélectionnez **suivant**.

1. Dans le **paramètres** page, sélectionnez le **paramètres avancés** onglet.

1. Allumez le **activer IntelliTrace** option pour collecter les journaux IntelliTrace pour votre application lorsqu’elle est publiée dans le cloud.
   
1. Pour personnaliser la configuration IntelliTrace initiale, sélectionnez **paramètres** regard **activer IntelliTrace**.

    ![Lien paramètres IntelliTrace](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/intellitrace-settings-link.png)
   
1. Dans le **paramètres IntelliTrace** boîte de dialogue, vous pouvez spécifier les événements au journal, si vous souhaitez collecter des informations sur les appels, les modules et les processus pour collecter les journaux, la quantité d’espace à allouer à l’enregistrement. Pour plus d’informations sur IntelliTrace, consultez [débogage avec IntelliTrace](http://go.microsoft.com/fwlink/?LinkId=214468).
   
    ![Paramètres IntelliTrace](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC519063.png)

Le fichier journal IntelliTrace est un fichier journal circulaire de la taille maximale spécifiée dans les paramètres IntelliTrace (la taille par défaut est 250 Mo). Les fichiers journaux IntelliTrace sont collectés dans un fichier du système de fichiers de la machine virtuelle. Lorsque vous demandez les journaux, un instantané est pris à ce stade dans le temps et téléchargé sur votre ordinateur local.

Une fois que le service cloud Azure a été publié sur Azure, vous pouvez déterminer si IntelliTrace a été activé à partir du nœud Azure dans **Explorateur de serveurs**, comme illustré dans l’image suivante :

![Explorateur de serveurs - IntelliTrace activé](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC744134.png)

## <a name="download-intellitrace-logs-for-a-role-instance"></a>Télécharger les journaux IntelliTrace pour une instance de rôle
À l’aide de Visual Studio, vous pouvez télécharger les fichiers journaux IntelliTrace pour une instance de rôle en suivant ces étapes :

1. Dans **Explorateur de serveurs**, développez le **Services Cloud** nœud, puis recherchez l’instance de rôle dont vous souhaitez télécharger les journaux. 

1. Cliquez sur l’instance de rôle, puis dans le menu contextuel, sélectionnez **afficher les journaux IntelliTrace**. 

    ![Afficher l’option de menu des journaux IntelliTrace](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/view-intellitrace-logs.png)

1. Les journaux IntelliTrace sont téléchargés vers un fichier dans un répertoire sur votre ordinateur local. Chaque fois que vous demandez la IntelliTrace enregistre, un nouvel instantané est créé. Bien que les journaux sont en cours de téléchargement, Visual Studio affiche la progression de l’opération dans le **journal d’activité Azure** fenêtre. Comme indiqué dans l’illustration suivante, vous pouvez développer l’élément de ligne pour afficher plus de détails de l’opération.

![VST_IntelliTraceDownloadProgress](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC745551.png)

Vous pouvez continuer à travailler dans Visual Studio pendant le téléchargement de sont les journaux IntelliTrace. Lorsque le journal de téléchargement est terminé, il s’ouvre dans Visual Studio.

> [!NOTE]
> Les journaux IntelliTrace peuvent contenir des exceptions que l’infrastructure génère et gère par la suite. Code d’infrastructure interne génère ces exceptions dans le cadre normal du démarrage d’un rôle, donc vous pouvez les ignorer en toute sécurité.
> 
> 

## <a name="next-steps"></a>Étapes suivantes
- [Options de débogage de services cloud Azure](vs-azure-tools-debugging-cloud-services-overview.md)
- [Publication d’un service cloud Azure à l’aide de Visual Studio](vs-azure-tools-publishing-a-cloud-service.md)