---
ms.technology: vs-ai-tools
ms.openlocfilehash: b941d0ba55c540de4bda1cb0f9c4ed18ceab524f
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2018
---
# <a name="browse-storage-to-upload-data-or-download-models-and-logs"></a>Parcourir le stockage pour charger des données ou télécharger des modèles et des journaux

Vous pouvez parcourir tout le stockage sur l’ordinateur distant ou le partage de fichier Azure pour activer le chargement de données ou le téléchargement de modèles et de journaux. Ou si vous souhaitez accéder aux journaux et résultats d’un travail spécifique, vous pouvez utiliser l’explorateur de travaux.

## <a name="to-access-all-data-on-the-remote-machine-or-file-share"></a>Pour accéder à toutes les données sur l’ordinateur distant ou le partage de fichiers
1. Ouvrir l’**Explorateur de serveurs**
2. Développer l’ordinateur distant ou le contexte de calcul Batch AI
3. Cliquer avec le bouton droit sur **Stockage**, puis cliquer sur **Parcourir**

    ![storage](media\manage-storage\browse-storage.png)

## <a name="to-access-job-specific-data-on-the-remote-machine-or-file-share"></a>Pour accéder à des données de travaux spécifiques sur l’ordinateur distant ou le partage de fichiers
1. Ouvrir l’[historique des travaux](job-details.md)
2. Sélectionner le travail
3. Cliquer sur **Dossier de travail** ou sur StdOut / Stderr pour un accès rapide à ces importants fichiers journaux

    ![storage](media\manage-storage\job-workingfolder.png)
