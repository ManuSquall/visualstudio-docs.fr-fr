---
title: Utilisation du gestionnaire de texte pour surveiller les paramètres globaux | Microsoft Docs
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
ms.openlocfilehash: ece51450b8344ae4715a912399ec538171a26a5c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695469"
---
# <a name="using-the-text-manager-to-monitor-global-settings"></a>Utilisation du gestionnaire de texte pour surveiller les paramètres globaux
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si vous implémentez un éditeur principal, vous devez surveiller les modifications apportées aux paramètres globaux, car ces modifications peuvent affecter votre instance de l’éditeur. Vous pouvez suivre les modifications en écoutant les événements déclenchés par le gestionnaire de texte. Par exemple, lorsque vous spécifiez une préférence globale pour l’apparence ou le comportement d’un composant dans l’éditeur principal, tel que son objet de données de document, le gestionnaire de texte stocke ces informations et les communique à tous les clients concernés.  
  
## <a name="text-manager-functions"></a>Fonctions du gestionnaire de texte  
 Le gestionnaire de texte déclenche des événements pour un certain nombre de paramètres, y compris les éléments suivants :  
  
- Si une mémoire tampon est sous contrôle de code source  
  
- Comment s’inscrire pour les notifications de modification de fichier  
  
- Comment effectuer le suivi des vues associées à certaines mémoires tampons  
  
- Préférences de colorisation du texte  
  
- Préférences de tabulation et d’espace  
  
  Les préférences qui sont propres à une langue donnée ne sont pas gérées par le gestionnaire de texte. Ces paramètres doivent être gérés par chaque service de langage.  
  
  La notification d’événements pour le gestionnaire de texte est fournie par l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents> interface. Implémentez cette interface sur votre objet client pour gérer les événements déclenchés par le gestionnaire de texte. Vous vous inscrivez à ces événements à l’aide de l' <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> interface sur le gestionnaire de texte.  
  
## <a name="see-also"></a>Voir aussi  
 [Dans l’éditeur de base](../extensibility/inside-the-core-editor.md)   
 [Fonctionnalités de l’éditeur](https://msdn.microsoft.com/bdac940d-1f14-4019-a01f-fd0bb3dc7198)
