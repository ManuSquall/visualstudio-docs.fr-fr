---
title: "Créer une installation hors connexion de Visual Studio | Microsoft Docs"
description: "Découvrez comment installer Visual Studio hors connexion."
ms.custom: 
ms.date: 08/30/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
- layout [Visual Studio]
ms.assetid: f8625d5e-f6ea-4db0-83c0-619b77fab3cf
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 402ba3bc2640ff9f4adb3c04982cb62394729a83
ms.sourcegitcommit: eb954434c34b4df6fd2264266381b23ce9e6204a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2017
---
# <a name="create-an-offline-installation-of-visual-studio-2017"></a>Créer une installation hors connexion de Visual Studio 2017

Nous avons conçu le programme d’installation de Visual Studio 2017 pour fonctionner correctement dans un large éventail de conditions réseau et informatiques.

- Avec le nouveau modèle basé sur les charges de travail, vous devez télécharger bien moins d’éléments qu’avec les versions antérieures de Visual Studio : 300 Mo pour la plus petite installation.
- Contrairement aux fichiers « ISO » génériques et aux fichiers .zip, nous téléchargeons uniquement les packages dont vous avez besoin pour votre ordinateur. Par exemple, nous ne téléchargeons pas de fichiers 64 bits si vous n’en avez pas besoin.
- Pendant le processus d’installation, nous essayons trois technologies de téléchargement différentes (WebClient, BITS et WinInet) pour réduire les interférences avec le logiciel antivirus et proxy.
- Les fichiers nécessaires à l’installation de Visual Studio étant distribués sur un réseau de distribution global, nous pouvons vous les faire parvenir à partir d’un serveur local.

Nous vous recommandons d’essayer le [programme d’installation web de Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocsOL). Nous pensons que vous trouverez son utilisation satisfaisante.

 > [!div class="button"]
 > [Télécharger Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocsOL)
<br/>

Si vous souhaitez procéder à une installation hors connexion parce que votre connexion Internet n’est pas disponible ou fiable, consultez [Installer Visual Studio 2017 dans des environnements réseau à faible bande passante ou non fiables](../install/install-vs-inconsistent-quality-network.md). Vous pouvez utiliser la ligne de commande pour créer un cache local des fichiers dont vous avez besoin pour effectuer l’installation hors connexion. Ce processus remplace les fichiers ISO des versions précédentes.

> [!NOTE]
> Si vous êtes administrateur d’entreprise et que vous souhaitez effectuer un déploiement de Visual Studio 2017 sur un réseau de stations de travail clientes qui sont protégées d’Internet par un pare-feu, consultez nos pages [Créer une installation réseau de Visual Studio 2017](../install/create-a-network-installation-of-visual-studio.md) et [Considérations particulières pour installer Visual Studio dans un environnement hors connexion](../install/install-visual-studio-in-offline-environment.md).

## <a name="get-support"></a>Obtenir de l’aide
Parfois, des problèmes peuvent se produire. Si votre installation de Visual Studio échoue, consultez la page [Résolution des problèmes d’installation et de mise à niveau de Visual Studio 2017](troubleshooting-installation-issues.md). Si aucune étape de résolution des problèmes ne vous aide, vous pouvez nous contacter pour une conversation en direct sur une assistance à l’installation (en anglais uniquement). Pour plus de détails, consultez la [page du support Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Voici d’autres options de support :
* Vous pouvez nous signaler des problèmes au niveau d’un produit via l’outil [Signaler un problème](../ide/how-to-report-a-problem-with-visual-studio-2017.md) qui s’affiche dans le programme d’installation de Visual Studio et dans l’IDE de Visual Studio.
* Vous pouvez nous faire part d’une suggestion de produit via [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Vous pouvez suivre les problèmes au niveau d’un produit sur le site [Visual Studio Developer Community](https://developercommunity.visualstudio.com/) et y poser des questions et obtenir des réponses.
* Vous pouvez également communiquer avec nous et d’autres développeurs Visual Studio en prenant part à notre [conversation Visual Studio dans la communauté Gitter ](https://gitter.im/Microsoft/VisualStudio)  (Cette option nécessite un compte [GitHub](https://github.com/)).
