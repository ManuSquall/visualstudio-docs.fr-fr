---
title: Activer les paramètres de sécurité ClickOnce | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- security [Visual Studio], ClickOnce applications
- ClickOnce deployment, security settings
- security settings, ClickOnce deployment
ms.assetid: 73cd3e9d-cd72-4ad2-8cae-94d6bb6b01e0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5f407ac42dc9997215bfe6682bb8b974b78c7847
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90850928"
---
# <a name="how-to-enable-clickonce-security-settings"></a>Guide pratique pour activer les paramètres de sécurité ClickOnce
La sécurité d’accès du code pour les applications ClickOnce doit être activée pour pouvoir publier l’application. Cela se fait automatiquement lorsque vous publiez une application à l’aide de l’Assistant Publication.

 Dans certains cas, l’activation de la sécurité d’accès du code peut avoir un impact sur les performances lors de la génération ou du débogage de votre application. dans ce cas, vous souhaiterez peut-être désactiver temporairement les paramètres de sécurité.

 Les paramètres de sécurité ClickOnce peuvent être activés ou désactivés dans la page **sécurité** du **Concepteur de projet**.

### <a name="to-enable-clickonce-security-settings"></a>Pour activer les paramètres de sécurité ClickOnce

1. Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.

2. Cliquez sur l’onglet **Security** .

3. Cochez la case **Activer les paramètres de sécurité ClickOnce** .

     Vous pouvez désormais personnaliser les paramètres de sécurité de votre application dans la page sécurité.

    > [!NOTE]
    > Cette case à cocher est automatiquement activée chaque fois que l’application est publiée à l’aide de l’Assistant **publication** .

### <a name="to-disable-clickonce-security-settings"></a>Pour désactiver les paramètres de sécurité ClickOnce

1. Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.

2. Cliquez sur l’onglet **Security** .

3. Désactivez la case à cocher **activer les paramètres de sécurité ClickOnce** .

     Votre application sera exécutée avec les paramètres de sécurité confiance totale ; tous les paramètres de la page **sécurité** seront ignorés.

    > [!NOTE]
    > Chaque fois que l’application est publiée avec l’Assistant publication, cette case à cocher est activée. vous devez le supprimer à nouveau après chaque publication réussie.

## <a name="see-also"></a>Voir aussi
- [Sécuriser des applications ClickOnce](../deployment/securing-clickonce-applications.md)
- [Sécurité d’accès du code pour les applications ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)
