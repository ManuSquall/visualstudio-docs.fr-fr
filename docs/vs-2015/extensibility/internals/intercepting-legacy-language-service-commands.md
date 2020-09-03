---
title: Interception des commandes du service de langage hérité | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, intercepting language service
- language services, intercepting commands
ms.assetid: eea69f03-349c-44bb-bd4f-4925c0dc3e55
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6510df2cc9cc1e504f09af033548e0d1c9b4ae74
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195013"
---
# <a name="intercepting-legacy-language-service-commands"></a>Interception des commandes du service de langage hérité
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Avec [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , vous pouvez faire en sorte que le service de langage intercepte les commandes que l’affichage de texte gérerait autrement. Cela est utile pour le comportement spécifique à la langue que l’affichage de texte ne gère pas. Vous pouvez intercepter ces commandes en ajoutant un ou plusieurs filtres de commande à la vue de texte à partir de votre service de langage.  
  
## <a name="getting-and-routing-the-command"></a>Obtention et routage de la commande  
 Un filtre de commande est un <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> objet qui surveille certaines séquences de caractères ou commandes clés. Vous pouvez associer plusieurs filtres de commande à un seul affichage de texte. Chaque vue de texte conserve une chaîne de filtres de commande. Après avoir créé un filtre de commande, ajoutez le filtre à la chaîne correspondant à la vue de texte appropriée.  
  
 Appelez la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> méthode sur le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> pour ajouter votre filtre de commande à la chaîne. Lorsque vous appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> , [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] retourne un autre filtre de commande auquel vous pouvez transmettre les commandes que votre filtre de commande ne gère pas.  
  
 Vous disposez des options suivantes pour la gestion des commandes :  
  
- Gérez la commande, puis transmettez la commande au filtre de commande suivant dans la chaîne.  
  
- Gérez la commande et ne transmettez pas la commande au filtre de commande suivant.  
  
- Ne gérez pas la commande, mais transmettez la commande au filtre de commande suivant.  
  
- Ignore la commande. Ne la gérez pas dans le filtre actuel et ne le transmettez pas au filtre suivant.  
  
  Pour plus d’informations sur les commandes que votre service de langage doit gérer, consultez [commandes importantes pour les filtres de service de langage](../../extensibility/internals/important-commands-for-language-service-filters.md).
