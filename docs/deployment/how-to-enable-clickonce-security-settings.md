---
title: 'Comment : activer les paramètres de sécurité ClickOnce | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f21b58a0ec9e8fe26cb02f72912fd23424cdfc7a
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/19/2018
ms.locfileid: "39150935"
---
# <a name="how-to-enable-clickonce-security-settings"></a>Comment : activer les paramètres de sécurité ClickOnce
Sécurité d’accès du code pour les applications ClickOnce doit être activée pour publier l’application. Cela se fait automatiquement lorsque vous publiez une application à l’aide de l’Assistant Publication.  
  
 Dans certains cas, l’activation de sécurité d’accès du code peut affecter les performances durant la génération ou de débogage de votre application ; Dans ce cas, vous pouvez désactiver temporairement les paramètres de sécurité.  
  
 Paramètres de sécurité ClickOnce peuvent être activés ou désactivés sur le **sécurité** page de la **Concepteur de projet**.  
  
### <a name="to-enable-clickonce-security-settings"></a>Pour activer les paramètres de sécurité ClickOnce  
  
1.  Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.  
  
2.  Cliquez sur l'onglet **Sécurité** .  
  
3.  Cochez la case **Activer les paramètres de sécurité ClickOnce** .  
  
     Vous pouvez maintenant personnaliser les paramètres de sécurité pour votre application dans la page sécurité.  
  
    > [!NOTE]
    >  Cette case à cocher est sélectionnée automatiquement chaque fois que l’application est publiée avec la **publier** Assistant.  
  
### <a name="to-disable-clickonce-security-settings"></a>Pour désactiver les paramètres de sécurité ClickOnce  
  
1.  Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.  
  
2.  Cliquez sur l'onglet **Sécurité** .  
  
3.  Effacer la **activer les paramètres de sécurité ClickOnce** case à cocher.  
  
     Votre application sera exécutée avec les paramètres de sécurité de confiance totale ; tous les paramètres de la **sécurité** page va être ignorée.  
  
    > [!NOTE]
    >  Chaque fois que l’application est publiée avec l’Assistant Publication, cette case à cocher sera sélectionnée ; Vous devez le désactiver à nouveau à chaque publication réussie.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécuriser les applications ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Sécurité d’accès du code pour les applications ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 
