---
title: Installation du kit de développement logiciel (SDK) Visual Studio | Microsoft Docs
description: Découvrez les options d’installation du kit de développement logiciel (SDK) de Visual Studio, notamment lors de l’installation de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 07/12/2018
ms.topic: overview
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f5b0d239c2280362b45c085448437b15bd8ddfe8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869529"
---
# <a name="install-the-visual-studio-sdk"></a>Installer le SDK Visual Studio

Le kit de développement logiciel (SDK) Visual Studio est une fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit de développement logiciel (SDK) Visual Studio plus tard.

## <a name="install-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Installer le kit de développement logiciel (SDK) Visual Studio dans le cadre d’une installation de Visual Studio

Pour inclure le kit de développement logiciel (SDK) dans votre installation de Visual Studio, installez la charge de travail **développement d’extension Visual Studio** sous d' **autres ensembles d’outils**. Cette charge de travail installe le kit de développement logiciel (SDK) Visual Studio et les composants requis. Pour affiner l’installation, vous pouvez sélectionner ou désélectionner des composants dans la vue **Résumé** .

## <a name="install-the-visual-studio-sdk-after-installing-visual-studio"></a>Installer le kit de développement logiciel (SDK) Visual Studio après l’installation de Visual Studio

Pour installer le kit de développement logiciel (SDK) Visual Studio après avoir terminé l’installation de Visual Studio, réexécutez le programme d’installation de Visual Studio et sélectionnez la charge de travail **développement d’extensions Visual Studio** .

## <a name="install-the-visual-studio-sdk-from-a-solution"></a>Installer le kit de développement logiciel (SDK) Visual Studio à partir d’une solution

Si vous ouvrez une solution avec un projet d’extensibilité sans installer au préalable le kit de développement logiciel (SDK) VS, une boîte de dialogue **installer la fonctionnalité manquante** vous est demandée pour installer la charge de travail développement de l' **extension Visual Studio** :

![Installer le développement d’extension](../extensibility/media/install-extension-development.png "Installer le développement d’extension")

## <a name="install-the-visual-studio-sdk-from-the-command-line"></a>Installer le kit de développement logiciel (SDK) Visual Studio à partir de la ligne de commande

Comme avec n’importe quelle charge de travail ou composant Visual Studio, vous pouvez également installer la charge de travail **développement d’extension Visual Studio** (ID : Microsoft. VisualStudio. Workload. VisualStudioExtension) à partir de la ligne de commande. Pour plus d’informations sur les commutateurs de ligne de commande et les instructions générales appropriées pour déterminer la charge de travail ou les identificateurs de composants, consultez [utiliser des paramètres de ligne de commande pour installer Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md) .

Notez que vous devez utiliser le programme d’installation de Visual Studio qui correspond à la version installée de Visual Studio. Par exemple, si vous avez Visual Studio Enterprise installé sur votre ordinateur, vous devez exécuter le programme d’installation Visual Studio Enterprise (*vs_enterprise.exe*).
