---
title: 'Comment : activer les paramètres de sécurité ClickOnce | Documents Microsoft'
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
ms.openlocfilehash: bc3f87e590c6b915d5b3d9db5d2517d80965dd6c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
ms.locfileid: "31558618"
---
# <a name="how-to-enable-clickonce-security-settings"></a>Comment : activer les paramètres de sécurité ClickOnce
Sécurité d’accès du code pour les applications ClickOnce doit être activée afin de publier l’application. Cette opération est effectuée automatiquement lorsque vous publiez une application à l’aide de l’Assistant de publication.  
  
 Dans certains cas, l’activation de la sécurité d’accès peut affecter les performances lors de la génération ou du débogage de votre application ; Dans ce cas, vous pouvez souhaiter désactiver temporairement les paramètres de sécurité.  
  
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
  
3.  Désactivez le **activer les paramètres de sécurité ClickOnce** case à cocher.  
  
     Votre application s’exécute avec les paramètres de sécurité de confiance totale ; tous les paramètres de la **sécurité** page sera ignorée.  
  
    > [!NOTE]
    >  Chaque fois que l’application est publiée avec l’Assistant Publication, cette case à cocher sera sélectionnée ; Vous devez le désactiver à nouveau à chaque publication réussie.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurisation des applications ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Sécurité d’accès du code pour les applications ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 
