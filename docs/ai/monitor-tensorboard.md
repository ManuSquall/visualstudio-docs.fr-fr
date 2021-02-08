---
title: Surveiller avec TensorBoard
description: Découvrez comment vous pouvez utiliser Visual Studio pour visualiser la progression de l’apprentissage de votre modèle avec TensorBoard.
ms.custom: SEO-VS-2020
author: jillre
ms.author: jillfra
manager: jmartens
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: edb6fe17902ad84ec6d7a6e5b9929bd965e7c29b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841391"
---
# <a name="monitor-with-tensorboard"></a>Surveiller avec TensorBoard

Vous pouvez visualiser la progression de la formation du modèle avec TensorBoard.

1. Cliquez avec le bouton droit sur votre projet et cliquez sur **Exécuter TensorBoard**, puis sélectionnez le répertoire de vos journaux TensorBoard de sortie.

    ![Capture d’écran de Visual Studio Explorateur de solutions avec le projet MNIST sélectionné. Un menu contextuel est ouvert et la commande exécuter TensorBoard est sélectionnée.](media/monitor-tensorboard/run-tensorboard.png)

2. Remarquez que les erreurs diminuent au fil du temps, ce qui signifie que la qualité s’améliore.

    ![Capture d’écran de la fenêtre principale TensorBoard montrant des visualisations graphiques de données à partir des journaux TensorBoard.](media/monitor-tensorboard/tensorboard.png)
