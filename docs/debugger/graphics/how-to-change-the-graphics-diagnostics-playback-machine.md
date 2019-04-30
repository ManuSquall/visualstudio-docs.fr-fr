---
title: 'Procédure : Modifier l’ordinateur de lecture Graphics Diagnostics | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1b9aa3ea-29a0-4e21-bc57-936f33537b5c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cd1f893874a9b0cfe1c7cd36f8e0bb1c38beaca1
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63388565"
---
# <a name="how-to-change-the-graphics-diagnostics-playback-machine"></a>Procédure : modifier l’ordinateur de lecture Graphics Diagnostics
Vous pouvez lire les informations graphiques à l’aide de votre ordinateur local, ou à l’aide d’un ordinateur distant ou un périphérique.

## <a name="choosing-a-playback-machine"></a>Choix d’un ordinateur de lecture
 L’ordinateur de lecture est un ordinateur ou un périphérique qui est utilisé pour lire les événements graphiques à partir d’un journal de graphisme. En règle générale, l’ordinateur local est l’option la plus pratique, mais un problème de rendu ne peut pas reproduire sur un ordinateur disposant d’un matériel différent ou des versions de pilote à l’ordinateur où elle a été capturée ; Dans ce cas, vous pouvez choisir un ordinateur de lecture à distance qui reproduit mieux le problème et toujours utiliser votre ordinateur de développement pour le diagnostiquer.

#### <a name="to-use-the-local-machine-to-play-back-graphics-information"></a>Pour utiliser l’ordinateur local pour lire les informations graphiques

1. Dans la fenêtre de document journal de graphisme, choisissez le **ordinateur de lecture** lien. Le **connexions au débogueur distant** boîte de dialogue s’affiche.

2. Sous **Configuration manuelle**, dans le **adresse** propriété, entrez `localhost`.

3. Définir le **Mode d’authentification** propriété **aucun**.

4. Choisissez le bouton **Sélectionner**.

#### <a name="to-use-a-remote-machine-to-play-back-graphics-information"></a>Pour utiliser un ordinateur distant pour lire les informations graphiques

1. Dans la fenêtre de document journal de graphisme, choisissez le **ordinateur de lecture** lien. Le **connexions au débogueur distant** boîte de dialogue s’affiche.

2. Sous **Configuration manuelle**, dans le **adresse** propriété, entrez le nom de domaine Windows ou l’adresse IP de l’ordinateur ou l’appareil que vous souhaitez utiliser pour lire les informations graphiques.

3. Spécifiez le type d’autorisation que vous souhaitez utiliser pour sécuriser la connexion à l’ordinateur de lecture.

    - Pour l’authentification Windows, définissez la **Mode d’authentification** propriété **Windows**.

    - Pour aucune authentification, définissez le **Mode d’authentification** propriété **aucun**.

4. Choisissez le bouton **Sélectionner**.

> [!NOTE]
> Le **connexions au débogueur distant** boîte de dialogue peut également s’afficher les cibles de débogage à distance qui sont directement connectés à votre ordinateur de développement ou qui sont sur le même sous-réseau. Vous pouvez utiliser une de ces cibles de débogage à distance en tant que l’ordinateur de lecture Graphics Diagnostics sans la configurer manuellement. Dans le **connexions au débogueur distant** boîte de dialogue, sélectionnez la cible que vous souhaitez, puis choisissez le **sélectionnez** bouton.

## <a name="see-also"></a>Voir aussi
- [Document journal de graphisme](graphics-log-document.md)