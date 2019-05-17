---
title: 'Procédure : Activer les paramètres de sécurité ClickOnce | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: e52acc18aa18873076df3d02071616c0399b1f33
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63407117"
---
# <a name="how-to-enable-clickonce-security-settings"></a>Procédure : Activer les paramètres de sécurité ClickOnce
Sécurité d’accès du code pour les applications ClickOnce doit être activée pour publier l’application. Cela se fait automatiquement lorsque vous publiez une application à l’aide de l’Assistant Publication.

 Dans certains cas, l’activation de sécurité d’accès du code peut affecter les performances durant la génération ou de débogage de votre application ; Dans ce cas, vous pouvez désactiver temporairement les paramètres de sécurité.

 Paramètres de sécurité ClickOnce peuvent être activés ou désactivés sur le **sécurité** page de la **Concepteur de projet**.

### <a name="to-enable-clickonce-security-settings"></a>Pour activer les paramètres de sécurité ClickOnce

1. Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.

2. Cliquez sur l'onglet **Sécurité** .

3. Cochez la case **Activer les paramètres de sécurité ClickOnce** .

     Vous pouvez maintenant personnaliser les paramètres de sécurité pour votre application dans la page sécurité.

    > [!NOTE]
    > Cette case à cocher est sélectionnée automatiquement chaque fois que l’application est publiée avec la **publier** Assistant.

### <a name="to-disable-clickonce-security-settings"></a>Pour désactiver les paramètres de sécurité ClickOnce

1. Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.

2. Cliquez sur l'onglet **Sécurité** .

3. Effacer la **activer les paramètres de sécurité ClickOnce** case à cocher.

     Votre application sera exécutée avec les paramètres de sécurité de confiance totale ; tous les paramètres de la **sécurité** page va être ignorée.

    > [!NOTE]
    > Chaque fois que l’application est publiée avec l’Assistant Publication, cette case à cocher sera sélectionnée ; Vous devez le désactiver à nouveau à chaque publication réussie.

## <a name="see-also"></a>Voir aussi
- [Sécuriser des applications ClickOnce](../deployment/securing-clickonce-applications.md)
- [Sécurité d’accès du code pour les applications ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)
