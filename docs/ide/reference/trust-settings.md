---
title: Paramètres d’approbation pour les fichiers et les dossiers
description: Découvrez comment modifier les paramètres d’approbation pour les fichiers et les dossiers de façon à conserver la sécurité de Visual Studio.
author: 2percentsilk
ms.author: allisb
ms.date: 09/05/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.PathTrustOptions
helpviewer_keywords:
- file security
- folder security
- mark of the web
- trusted files
- trusted folders
ms.openlocfilehash: 492a94962d255a9d18dcabdababf7fa6a540ada1
ms.sourcegitcommit: 935e1388281df0f04147802606b5cb7f513d45ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2020
ms.locfileid: "88197385"
---
# <a name="configure-trust-settings-for-files-and-folders"></a>Configurer les paramètres d’approbation pour les fichiers et les dossiers

Visual Studio demande une approbation de l’utilisateur avant d’ouvrir des projets qui ont la [marque du web](/previous-versions/windows/internet-explorer/ie-developer/compatibility/ms537628(v=vs.85)). Pour renforcer la sécurité, vous pouvez également configurer Visual Studio pour demander l’approbation de l’utilisateur avant d’ouvrir tout fichier ou dossier qui a la marque de l’attribut web, ou qui n’est pas désigné comme étant *approuvé*. Les vérifications des fichiers et des dossiers sont désactivées par défaut.

> [!WARNING]
> Vous devez toujours vérifier que le fichier, le dossier ou la solution provient d’une personne de confiance ou d’un emplacement approuvé avant de l’approuver.

## <a name="configure-trust-settings"></a>Configurer les paramètres d’approbation

Pour modifier les paramètres d’approbation, procédez comme suit :

1. Ouvrez **Outils**  >  **options**d'  >  **approbation paramètres** et sélectionnez le lien **configurer les paramètres d’approbation** dans le volet de droite.

2. Choisissez le niveau des vérifications que vous voulez pour les fichiers et les dossiers. Vous pouvez avoir des vérifications différentes pour chacun d’eux. Les options sont :

   * **Aucune vérification** : Visual Studio n’effectue aucune vérification.

   * **Vérifier la marque de l’attribut web**: si le fichier ou le dossier a la marque de l’attribut web, Visual Studio le bloque et demande l’autorisation de l’ouvrir.

   * **Vérifier que le chemin est approuvé** : si le chemin du fichier ou du dossier ne fait pas partie des **Chemins approuvés**, Visual Studio le bloque et demande l’autorisation de l’ouvrir.

   ![Options de vérification d’approbation](media/trust-settings.png)

## <a name="add-trusted-paths"></a>Ajouter des chemins approuvés

Pour ajouter des chemins approuvés, procédez comme suit :

1. Ouvrez **Outils**  >  **options**d'  >  **approbation paramètres** et sélectionnez le lien **configurer les paramètres d’approbation** dans le volet de droite.

2. Cliquez sur **Ajouter** dans la boîte de dialogue **Paramètres d’approbation**, puis sélectionnez **Fichier** ou **Dossier**.

3. Accédez au fichier ou au dossier que vous voulez ajouter à la liste approuvée et sélectionnez-le.

   Le chemin du fichier ou du dossier apparaît dans la liste **Chemins approuvés**.

   ![Chemins approuvés ajoutés](media/trusted-paths.png)

## <a name="remove-trusted-paths"></a>Supprimer des chemins approuvés

Pour supprimer des chemins approuvés, procédez comme suit :

1. Ouvrez **Outils**  >  **options**d'  >  **approbation paramètres** et sélectionnez le lien **configurer les paramètres d’approbation** dans le volet de droite.

2. Sélectionnez le chemin que vous voulez supprimer dans la liste **Chemins approuvés**, puis cliquez sur **Supprimer**.

   > [!TIP]
   > Pour sélectionner plusieurs entrées, maintenez enfoncée la touche **Maj** pendant que vous sélectionnez les chemins.

   Les chemins sélectionnés sont supprimés de la liste **Chemins approuvés**.
