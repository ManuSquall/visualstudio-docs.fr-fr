---
title: Le programme de mise à jour présente des erreurs lors de la récupération des informations
description: Instructions pour corriger l’erreur 'Erreur lors de la récupération des informations de mise à jour' dans Visual Studio 2019 pour Mac
author: asb3993
ms.author: amburns
ms.date: 04/13/2019
ms.technology: vs-ide-install
ms.assetid: 31AF914A-C66B-4CD3-9429-39695E0E94AE
ms.openlocfilehash: ef0d1f7516c410475f467ecaadecbb0aeaac71a3
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67825725"
---
# <a name="troubleshooting-updater-has-errors-retrieving-information"></a>Résolution des problèmes : Le programme de mise à jour présente des erreurs lors de la récupération des informations

Dans de rares cas, le message d’erreur « Erreur lors de la récupération des informations de mise à jour » peut s’afficher lorsque vous tentez de [mettre à jour Visual Studio pour Mac](update.md). Si cela se produit, essayez de corriger le problème en effectuant les étapes suivantes :

- Vérifiez votre connexion Internet. Une perte de connexion est la cause la plus courante de cette erreur.
  - Si vous ne parvenez pas à télécharger un composant, vous pouvez cliquer sur le bouton « retry » (ressayer) en regard du nom de composant pour relancer le téléchargement.
- Redémarrez l'environnement de développement intégré (IDE).
- Si vous continuez à voir ce message d’erreur, vous pouvez également tenter une mise à jour à l’aide du programme d’installation, si le fichier **.dmg** est toujours sur votre ordinateur, ou le télécharger depuis le site [visualstudio.com](https://visualstudio.microsoft.com/vs/mac/)
  - Le programme d’installation mettra à jour tous les composants installés sur votre ordinateur.
  - En réexécutant le programme d’installation, vous pourrez également installer les composants manquants que vous n’aviez pas encore installés.
- Vous pouvez également essayer d’effacer vos téléchargements mis en cache en supprimant le fichier situé dans `~/Library/Caches/VisualStudio/7.0/TempDownload/index.xml`.
