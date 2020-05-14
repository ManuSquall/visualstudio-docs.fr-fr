---
title: Intercepter les commandes de services linguistiques hérités (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, intercepting language service
- language services, intercepting commands
ms.assetid: eea69f03-349c-44bb-bd4f-4925c0dc3e55
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5206bced8b4bfae32498434765e5c3f61801b386
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707449"
---
# <a name="intercepting-legacy-language-service-commands"></a>Interception des commandes du service de langage hérité
Avec [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], vous pouvez avoir le service de langue intercepter les commandes que la vue de texte serait autrement gérer. Ceci est utile pour un comportement spécifique à la langue que la vue de texte ne gère pas. Vous pouvez intercepter ces commandes en ajoutant un ou plusieurs filtres de commande à la vue de texte de votre service linguistique.

## <a name="getting-and-routing-the-command"></a>Obtenir et router le commandement
 Un filtre de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> commande est un objet qui surveille certaines séquences de caractères ou commandes clés. Vous pouvez associer plus d’un filtre de commande à une seule vue de texte. Chaque vue de texte maintient une chaîne de filtres de commande. Après avoir créé un nouveau filtre de commande, vous ajoutez le filtre à la chaîne pour la vue de texte appropriée.

 Appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> la méthode <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> sur le pour ajouter votre filtre de commande à la chaîne. Lorsque vous <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] appelez, retourne un autre filtre de commande auquel vous pouvez passer les commandes que votre filtre de commande ne gère pas.

 Vous avez les options suivantes pour le traitement des commandes :

- Manipulez la commande, puis transmettez la commande au filtre de commande suivant de la chaîne.

- Manipulez la commande et ne transmettez pas la commande au filtre de commande suivant.

- Ne manipulez pas la commande, mais transmettez la commande au filtre de commande suivant.

- Ignorez la commande. Ne le manipulez pas dans le filtre actuel, et ne le transmettez pas au filtre suivant.

  Pour plus d’informations sur les commandes que votre service linguistique doit gérer, consultez [les commandes importantes pour les filtres de service linguistique](../../extensibility/internals/important-commands-for-language-service-filters.md).
