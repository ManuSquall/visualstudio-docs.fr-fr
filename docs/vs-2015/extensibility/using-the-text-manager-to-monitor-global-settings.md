---
title: Avec le Gestionnaire de texte pour surveiller les paramètres globaux | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - monitor global settings
- editors [Visual Studio SDK], legacy - text manager
ms.assetid: 023e7671-cf65-419c-9bc1-3c4ee92aa436
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 792c566eda53cb8a4703e8ab03982952c518d8e4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58948143"
---
# <a name="using-the-text-manager-to-monitor-global-settings"></a>Avec le Gestionnaire de texte pour surveiller les paramètres globaux
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
 [Fonctionnalités de l’éditeur](http://msdn.microsoft.com/bdac940d-1f14-4019-a01f-fd0bb3dc7198)
