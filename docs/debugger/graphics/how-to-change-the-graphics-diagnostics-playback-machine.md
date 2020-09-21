---
title: Modifier l’ordinateur de lecture des diagnostics Graphics
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 1b9aa3ea-29a0-4e21-bc57-936f33537b5c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a7b7f3f09495b760d4ee3ab8c20781bc337b1bb2
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810690"
---
# <a name="how-to-change-the-graphics-diagnostics-playback-machine"></a>Procédure : modifier l’ordinateur de lecture Graphics Diagnostics
Vous pouvez lire les informations graphiques à l’aide de votre ordinateur local ou à l’aide d’un ordinateur ou d’un appareil distant.

## <a name="choosing-a-playback-machine"></a>Choix d’un ordinateur de lecture
 L’ordinateur de lecture est un ordinateur ou un appareil utilisé pour lire les événements graphiques à partir d’un journal de graphisme. En règle générale, l’ordinateur local est l’option la plus pratique, mais un problème de rendu peut ne pas se reproduire sur un ordinateur dont la version du matériel ou du pilote est différente de celle de l’ordinateur sur lequel il a été capturé. dans ce cas, vous pouvez choisir un ordinateur de lecture à distance qui reproduit mieux le problème tout en continuant à utiliser votre ordinateur de développement pour le diagnostic.

#### <a name="to-use-the-local-machine-to-play-back-graphics-information"></a>Pour utiliser l’ordinateur local pour lire les informations graphiques

1. Dans la fenêtre de document du journal de graphisme, choisissez le lien de lecture de l' **ordinateur** . La boîte de dialogue **connexions du débogueur distant** s’affiche.

2. Sous **configuration manuelle**, dans la propriété **adresse** , entrez `localhost` .

3. Définissez la propriété **mode d’authentification** sur **aucun**.

4. Choisissez le bouton **Sélectionner**.

#### <a name="to-use-a-remote-machine-to-play-back-graphics-information"></a>Pour utiliser une machine distante pour lire des informations graphiques

1. Dans la fenêtre de document du journal de graphisme, choisissez le lien de lecture de l' **ordinateur** . La boîte de dialogue **connexions du débogueur distant** s’affiche.

2. Sous **configuration manuelle**, dans la propriété **adresse** , entrez le nom de domaine Windows ou l’adresse IP de l’ordinateur ou du périphérique que vous souhaitez utiliser pour lire les informations graphiques.

3. Spécifiez le type d’autorisation que vous souhaitez utiliser pour sécuriser la connexion à l’ordinateur de lecture.

    - Pour l’authentification Windows, définissez la propriété **mode d’authentification** sur **Windows**.

    - Pour aucune authentification, définissez la propriété **mode d’authentification** sur **aucun**.

4. Choisissez le bouton **Sélectionner**.

> [!NOTE]
> La boîte de dialogue **connexions du débogueur distant** peut également afficher des cibles de débogage distant qui sont directement connectées à votre ordinateur de développement ou qui se trouvent sur le même sous-réseau. Vous pouvez utiliser l’une de ces cibles de débogage distant en tant qu’ordinateur de lecture Graphics Diagnostics sans le configurer manuellement. Dans la boîte de dialogue **connexions du débogueur distant** , sélectionnez la cible souhaitée, puis cliquez sur le bouton **Sélectionner** .

## <a name="see-also"></a>Voir aussi
- [Document de journal Graphics](graphics-log-document.md)