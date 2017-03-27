---
title: "Résolution des problèmes de débogage à distance Azure avec Python Tools pour Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b723b343-dffb-457e-9af7-ee48c1451e30
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a42f5a30375192c89c9984e40ba0104da98d7253
ms.openlocfilehash: fcf44a3967c0bd391808c9f6b3a23f39aeff05fd
ms.lasthandoff: 03/07/2017

---

# <a name="remote-debugging-troubleshooter-for-python-and-azure"></a>Résolution des problèmes de débogage à distance pour Python et Azure

L’attachement de Visual Studio à un [service Azure App Service pour le débogage à distance](debugging-azure-remote.md) échouera pour l’une des raisons suivantes :

| Raison | Résolution |
| --- | --- |
| Vous n’avez pas installé Visual Studio 2013 Update 4 ou une version ultérieure. | Installez une version adéquate à partir de [visualstudio.com](https://www.visualstudio.com/downloads/). | 
| Le projet déployé sur App Service ne correspond pas à celui qui est ouvert dans Visual Studio. | Chargez le projet approprié dans Visual Studio. |
| Le projet n’a pas été déployé avec la configuration Débogage. | Redéployez l’application en cliquant avec le bouton droit sur le projet dans l’Explorateur de solutions et en sélectionnant **Publier**. Dans l’onglet **Paramètres**, assurez-vous que **Débogage** est la configuration sélectionnée. |
| App Service n’est pas en cours d’exécution. | Démarrez ce service à partir de l’Explorateur de serveurs dans Visual Studio ou à partir du Portail Azure. |
| App Service n’est pas configuré pour les sockets web. | Accédez au [Portail Azure](https://portal.azure.com), puis à votre App Service, ouvrez le panneau **Paramètres > Paramètres de l’application**, définissez **Paramètres généraux > Web sockets** sur **Activer**, puis sélectionnez **Enregistrer**. (Notez que les options **Débogage** présentées sur ce panneau ne s’appliquent *pas* au débogage Python.) |
| `web.debug.config` a été modifié pour désactiver le proxy de débogage. | Supprimez le fichier et republiez le projet sur App Service. Au cours de cette opération, Python Tools pour Visual Studio recrée le fichier. |

Voir aussi :

- [Débogage à distance Azure pour Python](debugging-azure-remote.md)

