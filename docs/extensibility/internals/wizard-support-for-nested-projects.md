---
title: Prise en charge de l’Assistant pour les projets imbriqués | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6fd9871e794c2968bab3effce0717ea1cae508eb
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56603961"
---
# <a name="wizard-support-for-nested-projects"></a>Prise en charge de l’Assistant pour les projets imbriqués
L’IDE exécute deux Assistants projet parent pour les projets imbriqués peut implémenter : le **nouveau projet** Assistant et le **ajouter un élément** Assistant.

 Si un utilisateur démarre la **nouveau projet** Assistant en sélectionnant **ajouter un projet** et en cliquant sur **nouveau projet** dans le menu fichier ou en sélectionnant **ajouter** et cliquant **nouveau projet** dans l’Explorateur de solutions, l’IDE exécute la **ajouter** commande et l’implémentation du projet parent de la **ajouter**renvoie un fichier de projet de modèle ou un fichier de l’Assistant (.vsz) qui dispose d’un ensemble de paramètres de contexte.

 De même, d’un projet parent mise en œuvre de **AddItem** Assistants retourne un fichier .vsz qui possède un ensemble différent de paramètres de contexte.

 Pour plus d’informations sur les Assistants, consultez [Assistant (. Fichier vsz)](../../extensibility/internals/wizard-dot-vsz-file.md), [paramètres de contexte](../../extensibility/internals/context-parameters.md) et [inscription Project and Item Templates](../../extensibility/internals/registering-project-and-item-templates.md).

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [Imbriquer des projets](../../extensibility/internals/nesting-projects.md)