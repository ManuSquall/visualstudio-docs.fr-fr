---
title: L’accès à des clouds privés Azure avec Visual Studio | Microsoft Docs
description: Découvrez comment accéder aux ressources de cloud privé à l’aide de Visual Studio.
author: ghogen
manager: douge
assetId: 9d733c8d-703b-44e7-a210-bb75874c45c8
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/13/2017
ms.author: ghogen
ms.openlocfilehash: 216b85e0ebf42b79c388ce217d548f2dce3c86b6
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002019"
---
# <a name="accessing-private-azure-clouds-with-visual-studio"></a>L’accès à des clouds privés Azure avec Visual Studio

Par défaut, Visual Studio prend en charge les points de terminaison REST cloud Azure. Dans cet article, vous allez apprendre à utiliser le certificat de votre cloud privé pour accéder et interagir avec le cloud privé à partir de Visual Studio.

1. Dans le portail Azure pour le cloud privé, téléchargez votre fichier de paramètres de publication, ou contactez votre administrateur pour un fichier de paramètres de publication. (Le fichier porte l’extension `.publishsettings`.)

1. Dans Visual Studio **Explorateur de serveurs**, cliquez sur le **Azure** nœud et sélectionnez **gérer et filtrer les abonnements**.

    ![Commande gérer les abonnements](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/IC790778.png)

1. Dans le **gérer les abonnements Microsoft Azure** boîte de dialogue, sélectionnez le **certificats** , puis sélectionnez **importation**.

    ![L’importation de certificats Azure](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/IC790779.png)

1. Dans le **importer les abonnements Microsoft Azure** boîte de dialogue, sélectionnez **Parcourir**.

    ![Bouton Parcourir dans la boîte de dialogue Importer les abonnements Microsoft Azure](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/browse-button.png)

1. Dans le **Open** boîte de dialogue, accédez au répertoire où vous avez enregistré le fichier de paramètres de publication, sélectionnez le fichier, puis cliquez **Open**.

    ![Sélectionnez le fichier de paramètres de publication](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/select-publish-settings-file.png)

1. Lorsque retournée à la **importer les abonnements Microsoft Azure** boîte de dialogue, sélectionnez **importation**.

    ![Importez le fichier de paramètres de publication](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/IC790780.png)

    Les certificats sont importés à partir du fichier de paramètres de publication dans Visual Studio, et vous pouvez maintenant interagir avec vos ressources de cloud privé.

