---
title: Publier une application Python sur Azure App Service
description: Options de publication d’une application Python sur Azure App Service, y compris le déploiement Git et les conteneurs pour Linux, ainsi que le déploiement vers IIS.
ms.date: 12/06/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.custom: seodec18
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: ea5a4d53302d19d11da819cac94bb620df3dab6f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53965747"
---
# <a name="publish-to-azure-app-service"></a>Publier sur Azure App Service

À l’heure actuelle, Python est pris en charge sur Azure App Service pour Linux, et vous pouvez publier des applications à l’aide du [déploiement Git](#publish-to-app-service-on-linux-using-git-deploy) et de [conteneurs](#publish-to-app-service-on-linux-using-containers), comme décrit dans cet article.

> [!Note]
> La prise en charge de Python sur Azure App Service pour Windows est officiellement déconseillée. Par conséquent, la commande **Publish** dans Visual Studio est officiellement prise en charge uniquement pour une [cible IIS](#publish-to-iis), et le débogage à distance sur Azure App Service n’est officiellement plus pris en charge.
>
> Toutefois, les fonctionnalités [Publication sur App Service sur Windows](publish-to-app-service-windows.md) fonctionnent toujours pour l’instant, tout comme les extensions Python pour App Service sur Windows qui restent disponibles mais ne seront pas dépannées ou mises à jour.

## <a name="publish-to-app-service-on-linux-using-git-deploy"></a>Publier sur App Service sur Linux à l’aide du déploiement Git

Le déploiement Git connecte un App Service sur Linux à une branche spécifique d’un référentiel Git. La validation du code pour cette branche exécute automatiquement le déploiement sur App Service, et App Service installe automatiquement toutes les dépendances répertoriées dans *requirements.txt*. Dans ce cas, App Service sur Linux exécute votre code dans une image de conteneur préconfigurée qui utilise le serveur web Gunicorn. À l’heure actuelle, ce service est en préversion et n’est pas pris en charge pour une utilisation en production.

Pour plus d'informations, consultez les articles suivants dans la documentation Azure :

- [Démarrage rapide : Créer une application web Python dans App Service](/azure/app-service/containers/quickstart-python?toc=%2Fpython%2Fazure%2FTOC.json) fournit une courte procédure pas à pas du processus de déploiement Git à l’aide d’une application Flask simple et d’un déploiement à partir d’un dépôt Git local.
- [Comment configurer Python](/azure/app-service/containers/how-to-configure-python) décrit les caractéristiques du conteneur App Service sur Linux et la façon de personnaliser la commande de démarrage Gunicorn pour votre application.

## <a name="publish-to-app-service-on-linux-using-containers"></a>Publier sur App Service sur Linux à l’aide de conteneurs

Au lieu d’utiliser le conteneur prégénéré avec App Service sur Linux, vous pouvez fournir votre propre conteneur. Cette option vous permet de choisir les serveurs web que vous utilisez et de personnaliser le comportement du conteneur.

Il existe deux options pour créer, gérer et envoyer (Push) les conteneurs :

- Utilisez Visual Studio Code et l’extension Docker, comme décrit dans [Déployer Python à l’aide de conteneurs Docker](https://code.visualstudio.com/docs/python/tutorial-deploy-containers). Même si vous n’utilisez pas Visual Studio Code, l’article fournit des détails utiles sur la création d’images de conteneurs pour les applications Flask et Django, à l’aide des serveurs web uwsgi et nginx prêts pour la production. Vous pouvez ensuite déployer ces mêmes conteneurs à l’aide d’Azure CLI.

- Utilisez la ligne de commande et Azure CLI, comme décrit dans [Utiliser une image Docker personnalisée](/azure/app-service/containers/tutorial-custom-docker-image) dans la documentation Azure. Toutefois, ce guide est générique et non spécifique à Python.

## <a name="publish-to-iis"></a>Publier sur IIS

À partir de Visual Studio, vous pouvez publier sur une machine virtuelle Windows ou autre ordinateur compatible IIS avec la commande **Publier**. Lorsque vous utilisez IIS, veillez à créer ou à modifier un fichier *web.config* dans l’application qui indique à IIS où trouver l’interpréteur Python. Pour plus d’informations, consultez [Configurer des applications web pour IIS](configure-web-apps-for-iis-windows.md).
