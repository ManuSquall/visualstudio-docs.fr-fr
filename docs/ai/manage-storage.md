---
ms.technology: vs-ai-tools
ms.openlocfilehash: 875bd78f6e1c6298d7f94360363dcf731cc3e992
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49874434"
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