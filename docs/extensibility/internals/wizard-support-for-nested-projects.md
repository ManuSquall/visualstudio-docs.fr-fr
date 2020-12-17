---
title: Prise en charge de l’Assistant pour les projets imbriqués | Microsoft Docs
description: Découvrez les deux assistants qu’un projet parent peut implémenter pour les projets imbriqués dans votre VSPackage dans le kit de développement logiciel (SDK) Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8b3c6dee712f79648eba203650cc70f76fcea657
ms.sourcegitcommit: d485b18e46ec4cf08704b5a8d0657bc716ec8393
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97615614"
---
# <a name="wizard-support-for-nested-projects"></a>Prise en charge de l’Assistant pour les projets imbriqués
L’IDE exécute deux assistants que le projet parent pour les projets imbriqués peut implémenter : l’Assistant **nouveau projet** et l’Assistant **Ajout d’élément** .

 Si un utilisateur démarre l’Assistant **nouveau projet** en sélectionnant **Ajouter un projet** et en cliquant sur **nouveau** projet dans le menu fichier ou en sélectionnant **Ajouter** et en cliquant avec le bouton droit sur **nouveau projet** dans Explorateur de solutions, l’IDE exécute la commande **AddProject** et l’implémentation du projet parent de la commande **AddProject** retourne un fichier projet de modèle ou un fichier Assistant (.

 De même, l’implémentation d’un projet parent d’assistants **AddItem** retourne un fichier. vsz qui a un ensemble différent de paramètres de contexte.

 Pour plus d’informations sur les assistants, consultez [Assistant (. Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md), les [paramètres de contexte](../../extensibility/internals/context-parameters.md) et l' [inscription des modèles de projet et d’élément](../../extensibility/internals/registering-project-and-item-templates.md).

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [Imbriquer des projets](../../extensibility/internals/nesting-projects.md)
