---
title: Interception des commandes du service de langage hérité | Microsoft Docs
description: Découvrez comment utiliser les filtres de commande dans Visual Studio pour intercepter les commandes du service de langage hérité et ajouter un comportement spécifique à la langue.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, intercepting language service
- language services, intercepting commands
ms.assetid: eea69f03-349c-44bb-bd4f-4925c0dc3e55
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c6a759f0cef7329d14d7d1472d38f662c0206448
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99839792"
---
# <a name="intercepting-legacy-language-service-commands"></a>Interception des commandes du service de langage hérité
Avec [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , vous pouvez faire en sorte que le service de langage intercepte les commandes que l’affichage de texte gérerait autrement. Cela est utile pour le comportement spécifique à la langue que l’affichage de texte ne gère pas. Vous pouvez intercepter ces commandes en ajoutant un ou plusieurs filtres de commande à la vue de texte à partir de votre service de langage.

## <a name="getting-and-routing-the-command"></a>Obtention et routage de la commande
 Un filtre de commande est un <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> objet qui surveille certaines séquences de caractères ou commandes clés. Vous pouvez associer plusieurs filtres de commande à un seul affichage de texte. Chaque vue de texte conserve une chaîne de filtres de commande. Après avoir créé un filtre de commande, ajoutez le filtre à la chaîne correspondant à la vue de texte appropriée.

 Appelez la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> méthode sur le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> pour ajouter votre filtre de commande à la chaîne. Lorsque vous appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> , [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] retourne un autre filtre de commande auquel vous pouvez transmettre les commandes que votre filtre de commande ne gère pas.

 Vous disposez des options suivantes pour la gestion des commandes :

- Gérez la commande, puis transmettez la commande au filtre de commande suivant dans la chaîne.

- Gérez la commande et ne transmettez pas la commande au filtre de commande suivant.

- Ne gérez pas la commande, mais transmettez la commande au filtre de commande suivant.

- Ignore la commande. Ne la gérez pas dans le filtre actuel et ne le transmettez pas au filtre suivant.

  Pour plus d’informations sur les commandes que votre service de langage doit gérer, consultez [commandes importantes pour les filtres de service de langage](../../extensibility/internals/important-commands-for-language-service-filters.md).
