---
title: Parcourir le stockage pour charger des données
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 7d0f2522117f4c5a5b85e99e2779d10cffcb7f22
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "72777410"
---
# <a name="browse-storage-to-upload-data-or-download-models-and-logs"></a>Parcourir le stockage pour charger des données ou télécharger des modèles et des journaux

Vous pouvez parcourir tout le stockage sur l’ordinateur distant ou le partage de fichier Azure pour activer le chargement de données ou le téléchargement de modèles et de journaux. Si vous voulez accéder aux sorties des journaux et des travaux, vous pouvez aussi utiliser l’Explorateur de travaux.

## <a name="to-access-all-data-on-the-remote-machine-or-file-share"></a>Pour accéder à toutes les données sur l’ordinateur distant ou le partage de fichiers

1. Ouvrez le **Server Explorer**.
2. Développez l’ordinateur distant ou le contexte de calcul Batch AI.
3. Cliquez avec le bouton droit sur **Stockage**, puis cliquez sur **Parcourir**.

    ![storage](media/manage-storage/browse-storage.png)

## <a name="to-access-job-specific-data-on-the-remote-machine-or-file-share"></a>Pour accéder à des données spécifiques à des travaux sur l’ordinateur distant ou sur le partage de fichiers

1. Ouvrir l’[historique des travaux](job-details.md)
2. Sélectionnez la tâche.
3. Cliquez **sur Working Folder** ou cliquez sur **StdOut / Stderr** pour un accès rapide à ces fichiers journaux importants.

    ![storage](media/manage-storage/job-workingfolder.png)
