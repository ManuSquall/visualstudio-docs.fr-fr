---
title: Résolution des problèmes de débogage à distance Azure pour Python
description: Guide pratique pour résoudre les problèmes durant une tentative de débogage d’une application Python exécutée dans Azure App Service à l’aide de Visual Studio.
ms.date: 06/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: f545fa223aa929b79016352e799d112bceddaf1c
ms.sourcegitcommit: 4f82c178b1ac585dcf13b515cc2a9cb547d5f949
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2018
ms.locfileid: "39341461"
---
# <a name="remote-debugging-troubleshooter-for-python-and-azure"></a>Résolution des problèmes de débogage à distance pour Python et Azure

L’attachement de Visual Studio à un [service Azure App Service pour le débogage à distance](debugging-remote-python-code-on-azure.md) échoue pour l’une des raisons suivantes :

| Raison | Résolution |
| --- | --- |
| Vous n’avez pas installé Visual Studio 2013 Update 4 ou une version ultérieure. | Installez une version adéquate à partir de [visualstudio.microsoft.com](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017). |
| Le projet déployé sur App Service ne correspond pas à celui qui est ouvert dans Visual Studio. | Chargez le projet approprié dans Visual Studio. |
| Le projet n’a pas été déployé avec la configuration **Débogage**. | Redéployez l’application en cliquant avec le bouton droit sur le projet dans **l’Explorateur de solutions** et en sélectionnant **Publier**. Dans l’onglet **Paramètres**, assurez-vous que **Débogage** est la configuration sélectionnée. |
| App Service n’est pas en cours d’exécution. | Démarrez ce service à partir de **l’Explorateur de serveurs** dans Visual Studio ou à partir du portail Azure. |
| App Service n’est pas configuré pour les sockets web. | Accédez au [portail Azure](https://portal.azure.com), puis à votre App Service, ouvrez le panneau **Paramètres** > **Paramètres de l’application**, définissez **Paramètres généraux** > **Web sockets** sur **Activer**, puis sélectionnez **Enregistrer**. (Notez que les options **Débogage** présentées sur ce panneau ne s’appliquent *pas* au débogage Python.) |
| *web.debug.config* a été modifié pour désactiver le proxy de débogage. | Supprimez le fichier et republiez le projet sur App Service. Durant cette opération, Visual Studio recrée le fichier. |

Voir aussi :

- [Débogage à distance Azure pour Python](debugging-remote-python-code-on-azure.md)
