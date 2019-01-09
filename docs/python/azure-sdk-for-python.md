---
title: Kit de développement logiciel (SDK) Azure pour Python
description: Le kit SDK Azure pour Python facilite l’utilisation des services Microsoft Azure à partir d’applications Python fonctionnant sur n’importe quelle plateforme.
ms.date: 12/06/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: db391b30305e3fad8384dcbeea611379f0061054
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53854215"
---
# <a name="consume-azure-services-using-the-azure-sdk-for-python"></a>Consommer les services Azure à l’aide du kit SDK Azure pour Python

Le kit SDK Azure pour Python facilite l’utilisation et la gestion des services Microsoft Azure à partir d’applications fonctionnant sur Windows, MacOS et Linux.

## <a name="installation"></a>Installation

Le Kit de développement logiciel (SDK) Azure est installé à partir de l’[Index des packages Python](https://pypi.python.org/pypi/azure).

Installez la **dernière version stable** (prise en charge de Python 2.7 et 3.x) comme suit :

```command
pip install azure
```

Vous pouvez également suivre les instructions d’[installation de Python et du Kit de développement logiciel SDK](https://docs.microsoft.com/azure/python-how-to-install/) de la documentation Azure.

## <a name="documentation"></a>Documentation

Le [kit SDK Azure pour le centre de développement Python](https://docs.microsoft.com/python/azure/?view=azure-python) dispose également d’un certain nombre de ressources utiles, y compris d’une série de didacticiels :

- [Création d’applications web sur Azure App Service dans Linux](/azure/app-service/containers/quickstart-python).
- [Stockage d’objets BLOB](/azure/storage/blobs/storage-quickstart-blobs-python)
- [Stockage de tables](/azure/cosmos-db/table-storage-how-to-use-python)
- [Stockage de file d’attente](/azure/storage/storage-python-how-to-use-queue-storage)
- [Azure Cosmos DB](/azure/cosmos-db/sql-api-python-application)
- [Files d’attente Service Bus](/azure/service-bus-messaging/service-bus-python-how-to-use-queues)
- [Rubriques/abonnements Service Bus](/azure/service-bus-messaging/service-bus-python-how-to-use-topics-subscriptions)
- [Gestion des services](/azure/cloud-services/cloud-services-python-how-to-use-service-management)

Pour les API publiques sans documentation, les tests unitaires du [référentiel GitHub du Kit de développement logiciel (SDK)](https://github.com/Azure/azure-sdk-for-python) constituent une bonne source d’informations :

- [Créer des tests d’unités](https://github.com/Azure/azure-storage-python/tree/master/tests)
- [Tests d’unités Service Bus](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-servicebus/tests)
- [Tests d’unités de gestion des services](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-servicemanagement-legacy/tests)

## <a name="support"></a>Assistance

Le référentiel GitHub pour le SDK se trouve à l’adresse [https://github.com/Azure/azure-sdk-for-python](https://github.com/Azure/azure-sdk-for-python).

[Signalez les problèmes au niveau du référentiel](https://github.com/Azure/azure-sdk-for-python/issues) si vous rencontrez des problèmes ou avez des questions concernant l’utilisation du Kit SDK.
