---
title: Interception des commandes de Service de langage hérité | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, intercepting language service
- language services, intercepting commands
ms.assetid: eea69f03-349c-44bb-bd4f-4925c0dc3e55
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: eb53de9cf4d3056d9a07a915267391de27b753fb
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56614907"
---
# <a name="intercepting-legacy-language-service-commands"></a>Interception des commandes du service de langage hérité
Avec [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], vous pouvez avoir les commandes d’ordonnée à l’origine de service de langage qui prendrait autrement en charge l’affichage de texte. Cela est utile pour le comportement spécifique au langage qui ne gère pas de l’affichage de texte. Vous pouvez intercepter ces commandes en ajoutant un ou plusieurs filtres de commande pour l’affichage de texte à partir de votre service de langage.

## <a name="getting-and-routing-the-command"></a>L’obtention et le routage de la commande
 Un filtre de commande est un <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> objet qui surveille certaines séquences de caractères ou les commandes de touches. Vous pouvez associer plusieurs filtres de commande à un affichage de texte unique. Chaque vue de texte conserve une chaîne de filtres de commande. Après avoir créé un nouveau filtre de commande, vous ajoutez le filtre à la chaîne pour l’affichage de texte appropriée.

 Appelez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> méthode sur le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> à ajouter votre filtre de commande à la chaîne. Lorsque vous appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] retourne un autre filtre de commande à laquelle vous pouvez passer les commandes que votre filtre de commande ne gère pas.

 Vous disposez des options suivantes pour la gestion des commandes :

- Gérer la commande, puis passer la commande au filtre de commande suivant dans la chaîne.

- Gérer la commande et ne transmettez pas de la commande au filtre de commande suivant.

- Ne gèrent pas la commande, mais passer la commande au filtre de commande suivant.

- Ignorer la commande. Ne les gèrent pas dans le filtre actuel et ne les transmettez pas au filtre suivant.

  Pour plus d’informations sur les commandes qui doit gérer votre service de langage, consultez [commandes importantes pour les filtres du Service de langage](../../extensibility/internals/important-commands-for-language-service-filters.md).