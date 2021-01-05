---
title: Parcourir le stockage pour charger des données
description: Découvrez comment vous pouvez parcourir tout le stockage sur l’ordinateur distant ou le partage de fichiers Azure pour activer le téléchargement de données ou le téléchargement de modèles et de journaux.
ms.custom: SEO-VS-2020
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: b145c4acf4047356b8996d09d746679900314f1b
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97726564"
---
# <a name="browse-storage-to-upload-data-or-download-models-and-logs"></a>Parcourir le stockage pour charger des données ou télécharger des modèles et des journaux

Vous pouvez parcourir tout le stockage sur l’ordinateur distant ou le partage de fichier Azure pour activer le chargement de données ou le téléchargement de modèles et de journaux. Si vous voulez accéder aux sorties des journaux et des travaux, vous pouvez aussi utiliser l’Explorateur de travaux.

## <a name="to-access-all-data-on-the-remote-machine-or-file-share"></a>Pour accéder à toutes les données sur l’ordinateur distant ou le partage de fichiers

1. Ouvrez le **Explorateur de serveurs**.
2. Développez l’ordinateur distant ou le contexte de calcul Batch AI.
3. Cliquez avec le bouton droit sur **Stockage**, puis cliquez sur **Parcourir**.

    ![Capture d’écran de Explorateur de serveurs avec le dossier machines distantes développé. Le stockage est mis en surbrillance dans l’arborescence des dossiers, et l’option Parcourir est sélectionnée dans le menu contextuel.](media/manage-storage/browse-storage.png)

## <a name="to-access-job-specific-data-on-the-remote-machine-or-file-share"></a>Pour accéder à des données spécifiques à des travaux sur l’ordinateur distant ou sur le partage de fichiers

1. Ouvrir l’[historique des travaux](job-details.md)
2. Sélectionnez la tâche.
3. Cliquez sur **dossier de travail** ou sur **stdout/stderr** pour accéder rapidement à ces fichiers journaux importants.

    ![Capture d’écran de la fenêtre de l’Explorateur de travaux dans Explorateur de serveurs. La tâche train_mnist est sélectionnée et le lien dossier de travail est sélectionné sous Détails du travail.](media/manage-storage/job-workingfolder.png)
