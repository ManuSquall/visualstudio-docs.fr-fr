---
title: Commutateur InstallVSTemplates de devenv.exe | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Devenv, /InstallVSTemplates switch
- /InstallVSTemplates Devenv switch
- InstallVSTemplates switch
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 529979caa801ace8dd649cf1614f2eeb27ca070b
ms.sourcegitcommit: d16c6812b114a8672a58ce78e6988b967498c747
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/02/2018
---
# <a name="installvstemplates-devenvexe"></a>/InstallVSTemplates (devenv.exe)

Le commutateur /InstallVSTemplates enregistre les modèles de projet ou d’élément qui se trouvent dans *\<Chemin d’installation de Visual Studio>*\Common7\IDE\ProjectTemplates\ ou *\<Chemin d’installation de Visual Studio>*\Common7\IDE\ItemTemplates\ pour qu’ils soient accessibles dans les boîtes de dialogue **Nouveau projet** et **Ajouter un nouvel élément**.

> [!WARNING]
> Ce commutateur est pris en charge uniquement pour le développement des partenaires Visual Studio. Vous devez exécuter devenv en tant qu’administrateur pour pouvoir utiliser les commutateurs [/Setup (devenv.exe)](../../ide/reference/setup-devenv-exe.md) et [/InstallVSTemplates (devenv.exe)](../../ide/reference/installvstemplates-devenv-exe.md). Pour plus d’informations, consultez [Autorisations de l’utilisateur](../../ide/user-permissions-and-visual-studio.md).

## <a name="syntax"></a>Syntaxe

```
devenv.exe /InstallVSTemplates
```

## <a name="see-also"></a>Voir aussi

[Commutateurs de la ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)