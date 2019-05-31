---
title: Installer le SDK Visual Studio | Microsoft Docs
ms.date: 07/12/2018
ms.topic: conceptual
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4208c20cc3e7da34efaf98af16f0f41d54613824
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340760"
---
# <a name="install-the-visual-studio-sdk"></a>Installer le SDK Visual Studio

Le SDK Visual Studio (Kit de développement logiciel) est une fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit SDK VS par la suite.

## <a name="install-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Installer le SDK Visual Studio en tant que partie d’une installation de Visual Studio

Pour inclure le SDK de Visual Studio dans votre installation de Visual Studio, vous devez installer le **développement d’extensions Visual Studio** charge de travail sous **autres ensembles d’outils**. Cette charge de travail va installer le SDK Visual Studio et la configuration requise. Vous pouvez affiner l’installation en sélectionnant ou désélectionnant les composants à partir de la **Résumé** vue.

## <a name="install-the-visual-studio-sdk-after-installing-visual-studio"></a>Installer le SDK Visual Studio après l’installation de Visual Studio

Pour installer le SDK Visual Studio après avoir effectué votre installation de Visual Studio, réexécutez le programme d’installation de Visual Studio et sélectionnez le **développement d’extensions Visual Studio** charge de travail.

## <a name="install-the-visual-studio-sdk-from-a-solution"></a>Installer le SDK Visual Studio à partir d’une solution

Si vous ouvrez une solution avec un projet d’extensibilité sans d’abord installer le Kit de développement Visual Studio, vous êtes invité par un **installer la fonctionnalité manquante** boîte de dialogue pour installer le **développement d’extensions Visual Studio** charge de travail :

![Installer le développement d’extensions](../extensibility/media/install-extension-development.png "installer le développement d’extensions")

## <a name="install-the-visual-studio-sdk-from-the-command-line"></a>Installer le SDK Visual Studio à partir de la ligne de commande

Comme avec toute charge de travail de Visual Studio ou le composant, vous pouvez également installer le **développement d’extensions Visual Studio** charge de travail (ID : Microsoft.VisualStudio.Workload.VisualStudioExtension) à partir de la ligne de commande. Consultez [utiliser des paramètres de ligne de commande pour installer Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md) pour plus d’informations sur les commutateurs de ligne de commande appropriés et obtenir des instructions générales sur la détermination des identificateurs de charge de travail ou composant.

Notez que vous devez utiliser le programme d’installation de Visual Studio qui correspond à votre version installée de Visual Studio. Par exemple, si vous avez Visual Studio Enterprise est installé sur votre ordinateur, vous devez exécuter le programme d’installation de Visual Studio Enterprise (*vs_enterprise.exe*).