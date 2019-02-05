---
title: Débogage d’un service cloud Azure publié avec IntelliTrace
description: Découvrez comment déboguer un service cloud avec Visual Studio et IntelliTrace
author: mikejo5000
manager: jillfra
ms.assetid: 5e6662fc-b917-43ea-bf2b-4f2fc3d213dc
ms.topic: conceptual
ms.custom: seodec18
ms.workload: azure-vs
ms.date: 03/21/2017
ms.author: mikejo
ms.prod: visual-studio-dev15
ms.openlocfilehash: b122b058d42be8970beeed3aa51957fd347d67ea
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55139767"
---
# <a name="debugging-a-published-azure-cloud-service-with-visual-studio-and-intellitrace"></a>Débogage d’un service cloud Azure publié avec Visual Studio et IntelliTrace
Avec IntelliTrace, vous pouvez enregistrer des informations de débogage détaillées pour une instance de rôle exécutée dans Azure. Si vous devez identifier la cause d’un problème, utilisez les journaux IntelliTrace pour exécuter pas à pas votre code à partir de Visual Studio comme s’il était exécuté dans Azure. En effet, IntelliTrace enregistre les principales données sur l’exécution du code et sur l’environnement quand votre application Azure est exécutée en tant que service cloud dans Azure. IntelliTrace vous permet d’examiner les données enregistrées à partir de Visual Studio.

Vous pouvez utiliser IntelliTrace si Visual Studio Enterprise est installé et que votre application Azure cible .NET Framework 4 ou une version ultérieure. IntelliTrace collecte des informations pour vos rôles Azure. Les machines virtuelles pour ces rôles exécutent toujours des systèmes d’exploitation 64 bits.

Vous pouvez également utiliser le [débogage distant](http://go.microsoft.com/fwlink/p/?LinkId=623041) pour l’attachement direct à un service cloud exécuté dans Azure.

> [!IMPORTANT]
> IntelliTrace est conçu uniquement pour des scénarios de débogage et ne doit pas être utilisé dans le cadre d’un déploiement de production.
>

## <a name="configure-an-azure-application-for-intellitrace"></a>Configurer une application Azure pour IntelliTrace
Pour activer IntelliTrace pour une application Azure, vous devez créer et publier l’application à partir d’un projet Azure Visual Studio. Configurez IntelliTrace pour votre application Azure avant de la publier dans Azure. Si vous publiez votre application sans configurer IntelliTrace, vous devez republier le projet. Pour plus d’informations, voir [Publication d’un projet Azure Cloud Services à l’aide de Visual Studio](http://go.microsoft.com/fwlink/p/?LinkId=623012).

1. Quand vous êtes prêt à déployer votre application Azure, vérifiez que les cibles de publication de votre projet sont définies sur **Debug**.

1. Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis, dans le menu contextuel, sélectionnez **Publier**.

1. Dans la boîte de dialogue **Publication d’application Azure**, sélectionnez l’abonnement Azure, puis sélectionnez **Suivant**.

1. Sur la page **Paramètres**, sélectionnez l’onglet **Paramètres avancés**.

1. Cochez l’option **Activer IntelliTrace** pour collecter des journaux IntelliTrace pour votre application publiée dans le cloud.

1. Pour personnaliser la configuration de base IntelliTrace, sélectionnez **Paramètres** en regard de l’option **Activer IntelliTrace**.

    ![Lien Paramètres IntelliTrace](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/intellitrace-settings-link.png)

1. Dans la boîte de dialogue **Paramètres IntelliTrace**, vous pouvez spécifier les événements à enregistrer dans le journal, si les informations d’appel doivent être collectées ou non, pour quels modules et processus collecter les journaux, et la quantité d’espace à allouer à l’enregistrement. Pour plus d’informations sur IntelliTrace, consultez [Débogage avec IntelliTrace](http://go.microsoft.com/fwlink/?LinkId=214468).

    ![Paramètres IntelliTrace](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC519063.png)

Le journal IntelliTrace est un fichier journal circulaire dont la taille maximale est spécifiée dans les paramètres IntelliTrace (la taille par défaut est de 250 Mo). Les journaux IntelliTrace sont regroupés dans un même fichier, situé dans le système de fichiers de la machine virtuelle. Quand vous demandez les journaux, un instantané est pris à ce moment précis, puis téléchargé vers votre ordinateur local.

Après avoir publié le service cloud Azure dans Azure, vous pouvez déterminer si IntelliTrace a été activé depuis le nœud Azure dans **l’Explorateur de serveurs**, comme indiqué dans l’illustration suivante :

![Explorateur de serveurs - IntelliTrace activé](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC744134.png)

## <a name="download-intellitrace-logs-for-a-role-instance"></a>Télécharger les journaux IntelliTrace pour une instance de rôle
À l’aide de Visual Studio, vous pouvez télécharger les journaux IntelliTrace pour une instance de rôle en procédant comme suit :

1. Dans **l’Explorateur de serveurs**, développez le nœud **Services cloud** et recherchez l’instance de rôle dont vous souhaitez télécharger les journaux.

1. Cliquez avec le bouton droit sur l’instance de rôle et dans le menu contextuel, sélectionnez **Afficher les journaux IntelliTrace**.

    ![Option de menu Afficher les fichiers journaux IntelliTrace](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/view-intellitrace-logs.png)

1. Les journaux IntelliTrace sont téléchargés et regroupés dans un fichier, situé dans un répertoire de votre ordinateur local. Chaque fois que vous demandez les journaux IntelliTrace, un nouvel instantané est créé. Visual Studio affiche la progression du téléchargement des journaux dans la fenêtre **Journal des activités Azure**. Comme le montre l’illustration ci-dessous, il est possible de développer la ligne correspondant à l’opération pour afficher plus de détails.

![VST_IntelliTraceDownloadProgress](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC745551.png)

Vous pouvez continuer à utiliser Visual Studio pendant le téléchargement des journaux IntelliTrace. Quand le téléchargement d’un journal est terminé, le journal s’ouvre dans Visual Studio.

> [!NOTE]
> Les journaux IntelliTrace peuvent contenir des exceptions que l’infrastructure génère et gère par la suite. Le code de l’infrastructure interne génère ces exceptions dans le cadre normal du démarrage d’un rôle. Vous pouvez donc les ignorer en toute sécurité.
>
>

## <a name="next-steps"></a>Étapes suivantes
- [Options de débogage d’Azure Cloud Services](vs-azure-tools-debugging-cloud-services-overview.md)
- [Publication d’un service cloud Azure à l’aide de Visual Studio](vs-azure-tools-publishing-a-cloud-service.md)