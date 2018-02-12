---
title: "Kit de développement logiciel (SDK) Azure pour Python | Microsoft Docs"
description: "Le kit SDK Azure pour Python facilite l’utilisation des services Microsoft Azure à partir d’applications Python fonctionnant sur n’importe quelle plateforme."
ms.custom: 
ms.date: 01/22/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: 
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: f4f42f80bef2548c8caaff84df0d9a0118bfeac7
ms.sourcegitcommit: ba29e4d37db92ec784d4acf9c6e120cf0ea677e9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2018
---
# <a name="azure-sdk-for-python"></a>Kit de développement logiciel (SDK) Azure pour Python

Le Kit de développement logiciel (SDK) Azure pour Python facilite l’utilisation et la gestion des services Microsoft Azure à partir d’applications fonctionnant sous Windows, Mac OSX et Linux.

## <a name="installation"></a>Installation

Le Kit de développement logiciel (SDK) Azure est installé à partir de l’[Index des packages Python](https://pypi.python.org/pypi/azure).

Installez la **dernière version stable** (prise en charge de Python 2.7 et 3.x) comme suit :

```command
pip install azure
```

Vous pouvez également suivre les instructions d’[installation de Python et du Kit de développement logiciel SDK](https://azure.microsoft.com/documentation/articles/python-how-to-install/) de la documentation Azure.

## <a name="documentation"></a>Documentation

Vous trouverez la documentation sur [azure-sdk-for-python.readthedocs.org](http://azure-sdk-for-python.readthedocs.org/en/latest/index.html).

Le [kit SDK Azure pour le centre de développement Python](http://azure.microsoft.com/develop/python/) dispose également d’un certain nombre de ressources utiles, y compris d’une série de didacticiels :

- Création d’applications web avec [Django](/azure/app-service-web/web-sites-python-create-deploy-django-app) [Flask](/azure/app-service-web/web-sites-python-create-deploy-flask-app) et [Bottle](/azure/app-service-web/web-sites-python-create-deploy-bottle-app).
- [Stockage d’objets BLOB](/azure/storage/storage-python-how-to-use-blob-storage)
- [Stockage de tables](/azure/storage/storage-python-how-to-use-table-storage)
- [Stockage de file d’attente](/azure/storage/storage-python-how-to-use-queue-storage)
- [DocumentDB](/azure/documentdb/documentdb-python-application)
- [Files d’attente Service Bus](/azure/service-bus-messaging/service-bus-python-how-to-use-queues)
- [Rubriques/abonnements Service Bus](/azure/service-bus-messaging/service-bus-python-how-to-use-topics-subscriptions)
- [Gestion des services](/azure/cloud-services/cloud-services-python-how-to-use-service-management)

Pour les API publiques sans documentation, les tests d’unités du [dépôt GitHub du SDK](https://github.com/Azure/azure-sdk-for-python) constituent une bonne source d’informations :

- [Créer des tests d’unités](https://github.com/Azure/azure-storage-python/tree/master/tests)
- [Tests d’unités Service Bus](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-servicebus/tests)
- [Tests d’unités de gestion des services](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-servicemanagement-legacy/tests)
- [Tests d’unités de gestion des ressources](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-mgmt/tests)

## <a name="support"></a>Assistance

Le référentiel Git du Kit de développement logiciel (SDK) se trouve à l’adresse suivante : [https://github.com/Azure/azure-sdk-for-python](https://github.com/Azure/azure-sdk-for-python).

[Signalez les problèmes au niveau du référentiel](https://github.com/Azure/azure-sdk-for-python/issues) si vous rencontrez des problèmes ou avez des questions concernant l’utilisation du Kit SDK.
