---
title: Soutien des sorciers aux projets imbriqués (fr) Microsoft Docs
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
ms.openlocfilehash: f7f37700d908167ebef8c071021558822bdce173
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703192"
---
# <a name="wizard-support-for-nested-projects"></a>Prise en charge de l’Assistant pour les projets imbriqués
L’IDE dirige deux assistants que le projet parent pour les projets imbriqués peuvent mettre en œuvre: le nouvel assistant **du projet** et **l’assistant Add Item.**

 Si un utilisateur démarre **l’assistant du nouveau projet** en sélectionnant **Add Project** et en cliquant sur **new Project** sur le menu Du fichier ou en sélectionnant **Add** and right-clicking **New Project** in Solution Explorer, l’IDE exécute la commande **AddProject** et la mise en œuvre de la commande **AddProject** par le projet parent renvoie un fichier de projet de modèle ou un fichier assistant (.vsz) qui a un ensemble de paramètres contextuelles.

 De même, la mise en œuvre par un projet parent des assistants **AddItem** renvoie un fichier .vsz qui a un ensemble différent de paramètres de contexte.

 Pour plus d’informations sur les sorciers, voir [Wizard (. Vsz) Fichier](../../extensibility/internals/wizard-dot-vsz-file.md), [Paramètres contextuelles](../../extensibility/internals/context-parameters.md) et [enregistrement des modèles de projets et d’objets](../../extensibility/internals/registering-project-and-item-templates.md).

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [Imbriquer des projets](../../extensibility/internals/nesting-projects.md)
