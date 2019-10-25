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
ms.sourcegitcommit: 57bc1c3887838d707c13feff72a677b3bad3be4b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72777410"
---
# <a name="browse-storage-to-upload-data-or-download-models-and-logs"></a>Parcourir le stockage pour charger des données ou télécharger des modèles et des journaux

Vous pouvez parcourir tout le stockage sur l’ordinateur distant ou le partage de fichier Azure pour activer le chargement de données ou le téléchargement de modèles et de journaux. Si vous voulez accéder aux sorties des journaux et des travaux, vous pouvez aussi utiliser l’Explorateur de travaux.

## <a name="to-access-all-data-on-the-remote-machine-or-file-share"></a>Pour accéder à toutes les données sur l’ordinateur distant ou le partage de fichiers

1. Ouvrir **l’Explorateur de serveurs**.
2. Développez l’ordinateur distant ou le contexte de calcul Batch AI.
3. Cliquez avec le bouton droit sur **Stockage**, puis cliquez sur **Parcourir**.

    ![storage](media/manage-storage/browse-storage.png)

## <a name="to-access-job-specific-data-on-the-remote-machine-or-file-share"></a>Pour accéder à des données spécifiques à des travaux sur l’ordinateur distant ou sur le partage de fichiers

1. Ouvrir l’[historique des travaux](job-details.md)
2. Sélectionnez le travail.
3. Cliquez sur **Dossier de travail** ou sur **StdOut / Stderr** pour accéder rapidement à ces fichiers journaux importants.

    ![storage](media/manage-storage/job-workingfolder.png)
