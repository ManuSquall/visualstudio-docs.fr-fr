---
title: Accès aux clouds Azure privés
description: Découvrez comment accéder aux ressources de cloud privé à l'aide de Visual Studio.
author: ghogen
manager: jillfra
assetId: 9d733c8d-703b-44e7-a210-bb75874c45c8
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 11/13/2017
ms.author: ghogen
ms.openlocfilehash: 6c1b46e34c688f232ee1f774ff2d19fdad7ff6bf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85280386"
---
# <a name="accessing-private-azure-clouds-with-visual-studio"></a>Accès à des clouds privés Azure avec Visual Studio

Par défaut, Visual Studio prend en charge les points de terminaison REST du cloud Azure. Cet article explique comment utiliser votre certificat de cloud privé pour accéder au cloud privé et y interagir à partir de Visual Studio.

1. Dans le portail Azure du cloud privé, téléchargez votre fichier de paramètres de publication ou contactez votre administrateur pour obtenir un fichier de paramètres de publication. (Le fichier comporte l'extension `.publishsettings`.)

1. Dans l’**Explorateur de serveurs** de Visual Studio, cliquez avec le bouton droit sur le nœud **Azure**, puis sélectionnez **Gérer et filtrer les abonnements**.

    ![Commande Gérer les abonnements](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/IC790778.png)

1. Dans la boîte de dialogue **Gérer les abonnements Microsoft Azure**, sélectionnez l’onglet **Certificats**, puis le bouton **Importer**.

    ![Importation de certificats Azure](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/IC790779.png)

1. Dans la boîte de dialogue **Importer les abonnements Microsoft Azure**, sélectionnez **Parcourir**.

    ![Bouton Parcourir dans la boîte de dialogue Importer les abonnements Microsoft Azure](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/browse-button.png)

1. Dans la boîte de dialogue **Ouvrir**, parcourez le répertoire dans lequel vous avez enregistré le fichier de paramètres de publication, sélectionnez ce dernier, puis cliquez sur **Ouvrir**.

    ![Sélection du fichier de paramètres de publication](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/select-publish-settings-file.png)

1. Lorsque vous revenez à la boîte de dialogue **Importer les abonnements Microsoft Azure**, sélectionnez **Importer**.

    ![Importation du fichier de paramètres de publication](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/IC790780.png)

    Les certificats sont importés du fichier de paramètres de publication vers Visual Studio. Vous pouvez maintenant interagir avec vos ressources de cloud privé.
