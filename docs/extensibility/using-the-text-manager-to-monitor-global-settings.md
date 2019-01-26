---
title: Avec le Gestionnaire de texte pour surveiller les paramètres globaux | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - monitor global settings
- editors [Visual Studio SDK], legacy - text manager
ms.assetid: 023e7671-cf65-419c-9bc1-3c4ee92aa436
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 29f054a5b584f7cf5471e783d28e857994c1a5a2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54989365"
---
# <a name="use-the-text-manager-to-monitor-global-settings"></a>Utilisez le Gestionnaire de texte pour surveiller les paramètres globaux
Si vous implémentez un éditeur de base, vous devez surveiller les modifications apportées aux paramètres globaux, étant donné que ces modifications peuvent affecter votre instance de l’éditeur. Vous pouvez suivre les modifications en écoutant les événements déclenchés par le Gestionnaire de texte. Par exemple, lorsque vous spécifiez une préférence globale pour l’apparence ou le comportement d’un composant dans l’éditeur principal, telles que son objet de données de document, le Gestionnaire de texte stocke ces informations et il communique avec tous les clients affectés.  
  
## <a name="text-manager-functions"></a>Fonctions de gestionnaire de texte  
 Le Gestionnaire de texte déclenche des événements pour un certain nombre de paramètres, y compris les éléments suivants :  
  
- Si une mémoire tampon est sous contrôle de code source  
  
- Comment s’inscrire aux notifications de modification de fichier  
  
- Comment effectuer le suivi des vues sont associées à certaines mémoires tampons  
  
- Préférences de la colorisation de texte  
  
- Onglet par rapport aux préférences de l’espace  
  
  Les préférences sont uniques à un langage donné ne sont pas gérés par le Gestionnaire de texte. Ces paramètres doivent être gérés par chaque service de langage.  
  
  Notification d’événement pour le Gestionnaire de texte est fournie par le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents> interface. Implémentez cette interface sur votre client pour gérer des événements a déclenché le Gestionnaire de texte. Vous inscrire pour ces événements en utilisant le <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> interface sur le Gestionnaire de texte.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’intérieur de l’éditeur principal](../extensibility/inside-the-core-editor.md)   
 [Fonctionnalités de l’éditeur](https://msdn.microsoft.com/library/bdac940d-1f14-4019-a01f-fd0bb3dc7198)