---
title: "Résolution des problèmes de débogage à distance Azure pour Python dans Visual Studio | Microsoft Docs"
description: "Guide pratique pour résoudre les problèmes durant une tentative de débogage d’une application Python exécutée dans Azure App Service à l’aide de Visual Studio."
ms.custom: 
ms.date: 07/12/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: 
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: b183cab67e8ac9382808832fb5c2c1e5283e70c0
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="remote-debugging-troubleshooter-for-python-and-azure"></a>Résolution des problèmes de débogage à distance pour Python et Azure

L’attachement de Visual Studio à un [service Azure App Service pour le débogage à distance](debugging-remote-python-code-on-azure.md) échoue pour l’une des raisons suivantes :

| Raison | Résolution |
| --- | --- |
| Vous n’avez pas installé Visual Studio 2013 Update 4 ou une version ultérieure. | Installez une version adéquate à partir de [visualstudio.com](https://www.visualstudio.com/downloads/). | 
| Le projet déployé sur App Service ne correspond pas à celui qui est ouvert dans Visual Studio. | Chargez le projet approprié dans Visual Studio. |
| Le projet n’a pas été déployé avec la configuration Débogage. | Redéployez l’application en cliquant avec le bouton droit sur le projet dans l’Explorateur de solutions et en sélectionnant **Publier**. Dans l’onglet **Paramètres**, assurez-vous que **Débogage** est la configuration sélectionnée. |
| App Service n’est pas en cours d’exécution. | Démarrez ce service à partir de l’Explorateur de serveurs dans Visual Studio ou à partir du Portail Azure. |
| App Service n’est pas configuré pour les sockets web. | Accédez au [Portail Azure](https://portal.azure.com), puis à votre App Service, ouvrez le panneau **Paramètres > Paramètres de l’application**, définissez **Paramètres généraux > Web sockets** sur **Activer**, puis sélectionnez **Enregistrer**. (Notez que les options **Débogage** présentées sur ce panneau ne s’appliquent *pas* au débogage Python.) |
| `web.debug.config` a été modifié pour désactiver le proxy de débogage. | Supprimez le fichier et republiez le projet sur App Service. Durant cette opération, Visual Studio recrée le fichier. |

Voir aussi :

- [Débogage à distance Azure pour Python](debugging-remote-python-code-on-azure.md)
