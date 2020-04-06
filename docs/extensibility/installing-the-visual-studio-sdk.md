---
title: Installation du Studio Visuel SDK (fr) Microsoft Docs
ms.date: 07/12/2018
ms.topic: conceptual
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2f391708abbd8a9b66f2dfd5aaa6559cb075910d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710349"
---
# <a name="install-the-visual-studio-sdk"></a>Installer le SDK Visual Studio

Le Visual Studio SDK (Software Development Kit) est une fonctionnalité facultative dans la configuration Visual Studio. Vous pouvez également installer le VS SDK plus tard.

## <a name="install-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Installer le Studio Visuel SDK dans le cadre d’une installation Visual Studio

Pour inclure le VS SDK dans votre installation Visual Studio, installez la charge de travail **de développement d’extension Visual Studio** sous **d’autres toolsets**. Cette charge de travail installera le Visual Studio SDK et les conditions préalables nécessaires. Vous pouvez affiner l’installation en sélectionnant ou en désélectionnant les composants de la vue **sommaire.**

## <a name="install-the-visual-studio-sdk-after-installing-visual-studio"></a>Installer le Studio Visuel SDK après l’installation de Visual Studio

Pour installer le Studio Visuel SDK après avoir terminé votre installation Visual Studio, réexécutez l’installateur Visual Studio et sélectionnez la charge de travail **de développement d’extension Visual Studio.**

## <a name="install-the-visual-studio-sdk-from-a-solution"></a>Installer le Studio Visuel SDK à partir d’une solution

Si vous ouvrez une solution avec un projet d’extensibility sans avoir d’abord installé le VS SDK, vous serez invité par un dialogue **Install Missing Feature** pour installer la charge de travail de développement **d’extension Visual Studio** :

![Installer le développement de l’extension](../extensibility/media/install-extension-development.png "Installer le développement de l’extension")

## <a name="install-the-visual-studio-sdk-from-the-command-line"></a>Installer le Studio Visuel SDK de la ligne de commande

Comme avec n’importe quelle charge de travail ou composant Visual Studio, vous pouvez également installer la charge de travail de **développement d’extension Visual Studio** (ID: Microsoft.VisualStudio.Workload.VisualStudioExtension) à partir de la ligne de commande. Consultez [les paramètres de la ligne de commande Utiliser pour installer Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md) pour plus de détails sur les commutateurs de ligne de commande appropriés et les instructions générales sur la détermination de la charge de travail ou des identificateurs de composants.

Notez que vous devez utiliser l’installateur Visual Studio qui correspond à votre version installée de Visual Studio. Par exemple, si vous avez Visual Studio Enterprise installé sur votre ordinateur, vous devez exécuter l’installateur Visual Studio Enterprise (*vs_enterprise.exe*).
