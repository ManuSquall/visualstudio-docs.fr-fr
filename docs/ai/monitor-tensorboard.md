---
title: Surveiller avec TensorBoard
description: Découvrez comment vous pouvez utiliser Visual Studio pour visualiser la progression de l’apprentissage de votre modèle avec TensorBoard.
ms.custom: SEO-VS-2020
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: 650189c4418355ae06b296bac7e16eece0ea88ad
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727253"
---
# <a name="monitor-with-tensorboard"></a>Surveiller avec TensorBoard

Vous pouvez visualiser la progression de la formation du modèle avec TensorBoard.

1. Cliquez avec le bouton droit sur votre projet et cliquez sur **Exécuter TensorBoard**, puis sélectionnez le répertoire de vos journaux TensorBoard de sortie.

    ![Capture d’écran de Visual Studio Explorateur de solutions avec le projet MNIST sélectionné. Un menu contextuel est ouvert et la commande exécuter TensorBoard est sélectionnée.](media/monitor-tensorboard/run-tensorboard.png)

2. Remarquez que les erreurs diminuent au fil du temps, ce qui signifie que la qualité s’améliore.

    ![Capture d’écran de la fenêtre principale TensorBoard montrant des visualisations graphiques de données à partir des journaux TensorBoard.](media/monitor-tensorboard/tensorboard.png)
