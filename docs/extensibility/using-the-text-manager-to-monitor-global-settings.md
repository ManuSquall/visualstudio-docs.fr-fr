---
title: À l’aide du Gestionnaire de texte pour surveiller des paramètres globaux | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - monitor global settings
- editors [Visual Studio SDK], legacy - text manager
ms.assetid: 023e7671-cf65-419c-9bc1-3c4ee92aa436
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e6c61a6859a2e8d359b2185ce959aa941944380f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="using-the-text-manager-to-monitor-global-settings"></a>À l’aide du Gestionnaire de texte pour surveiller des paramètres globaux
Si vous implémentez un éditeur principal, vous devez surveiller les modifications apportées aux paramètres globaux, étant donné que ces modifications peuvent affecter votre instance de l’éditeur. Vous pouvez suivre les modifications en écoutant les événements déclenchés par le Gestionnaire de texte. Par exemple, lorsque vous spécifiez une préférence globale pour l’apparence ou le comportement d’un composant dans l’éditeur de base, telles que l’objet de données de document, le Gestionnaire de texte stocke ces informations et communique à tous les clients concernés.  
  
## <a name="text-manager-functions"></a>Fonctions de gestionnaire de texte  
 Le Gestionnaire de texte déclenche des événements pour un nombre de paramètres, y compris les éléments suivants :  
  
-   Si une mémoire tampon est sous contrôle de code source  
  
-   Comment s’inscrire aux notifications de modification de fichier  
  
-   Comment effectuer le suivi des vues sont associées à certaines mémoires tampons  
  
-   Préférences de colorisation de texte  
  
-   Onglet par rapport aux préférences de l’espace  
  
 Préférences qui sont propres à une langue donnée ne sont pas gérés par le Gestionnaire de texte. Ces paramètres doivent être gérés par chaque service de langage.  
  
 Notification d’événement pour le Gestionnaire de texte est fournie par le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents> interface. Implémentez cette interface sur votre client pour gérer des événements a déclenché le Gestionnaire de texte. Vous inscrivez pour ces événements à l’aide de la <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> interface sur le Gestionnaire de texte.  
  
## <a name="see-also"></a>Voir aussi  
 [Dans l’éditeur de base](../extensibility/inside-the-core-editor.md)   
 [Fonctionnalités de l’éditeur](http://msdn.microsoft.com/en-us/bdac940d-1f14-4019-a01f-fd0bb3dc7198)