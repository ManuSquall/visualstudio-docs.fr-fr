---
title: Créer une installation hors connexion de Visual Studio
description: Découvrez comment installer Visual Studio hors connexion.
ms.custom: ''
ms.date: 01/17/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
- layout [Visual Studio]
ms.assetid: f8625d5e-f6ea-4db0-83c0-619b77fab3cf
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d19eabe10234ca2a1670ae04f99a45a85a6cac14
ms.sourcegitcommit: 6b092e7d466377f06913d49d183dbbdca16730f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2018
ms.locfileid: "43138875"
---
# <a name="create-an-offline-installation-of-visual-studio-2017"></a>Créer une installation hors connexion de Visual Studio 2017

Nous avons conçu le programme d’installation de Visual Studio 2017 pour fonctionner correctement dans un large éventail de conditions réseau et informatiques.

- Avec le nouveau modèle basé sur les charges de travail, vous devez télécharger bien moins d’éléments qu’avec les versions antérieures de Visual Studio : 300 Mo pour la plus petite installation.
- Contrairement aux fichiers « ISO » génériques et aux fichiers .zip, nous téléchargeons uniquement les packages dont vous avez besoin pour votre ordinateur. Par exemple, nous ne téléchargeons pas de fichiers 64 bits si vous n’en avez pas besoin.
- Pendant le processus d’installation, nous essayons trois technologies de téléchargement différentes (WebClient, BITS et WinInet) pour réduire les interférences avec le logiciel antivirus et proxy.
- Les fichiers nécessaires à l’installation de Visual Studio étant distribués sur un réseau de distribution global, nous pouvons vous les faire parvenir à partir d’un serveur local.

Nous vous recommandons d’essayer le [programme d’installation web de Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017). Nous pensons que vous trouverez son utilisation satisfaisante.

 > [!div class="button"]
 > [Télécharger Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)

Si vous souhaitez procéder à une installation hors connexion parce que votre connexion Internet n’est pas disponible ou fiable, consultez [Installer Visual Studio 2017 dans des environnements réseau à faible bande passante ou non fiables](../install/install-vs-inconsistent-quality-network.md). Vous pouvez utiliser la ligne de commande pour créer un cache local des fichiers dont vous avez besoin pour effectuer l’installation hors connexion. Ce processus remplace les fichiers ISO des versions précédentes.

> [!NOTE]
> Si vous êtes administrateur d’entreprise et que vous souhaitez effectuer un déploiement de Visual Studio 2017 sur un réseau de stations de travail clientes qui sont protégées d’Internet par un pare-feu, consultez nos pages [Créer une installation réseau de Visual Studio 2017](../install/create-a-network-installation-of-visual-studio.md) et [Installer les certificats nécessaires à l’installation hors connexion de Visual Studio](../install/install-certificates-for-visual-studio-offline.md).

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]
