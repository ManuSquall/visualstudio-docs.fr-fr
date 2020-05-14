---
title: Contexte du projet (en anglais seulement) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 51e411f0bca361f96cdffcfd89498908fd21d441
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706584"
---
# <a name="project-context"></a>Contexte de projet
Lorsque l’utilisateur ajoute ou travaille avec des projets et des éléments de projet, l’IDE utilise la notion de contexte de projet pour déterminer comment diverses opérations doivent être effectuées.

 En règle générale, les fichiers sont les objets de projet standard que l’utilisateur crée explicitement en sélectionnant la commande **du nouveau projet** ou mis à disposition en sélectionnant la commande Open **Project** sur le menu **Fichier.** Dans ces cas, les fichiers sont créés et ouverts dans le cadre d’un projet et le type de projet définit le contexte de la modification du document.

 Certains projets offrent un contexte très riche. Par exemple, le projet gère un espace de nom programmatique ou une connexion de base de données de portée de projet pour la liaison des données. L’utilisateur peut fréquemment ouvrir des fichiers ou des connexions de base de données directement à l’aide d’un objet de projet particulier, tel qu’un élément de projet affiché dans Solution Explorer.

 À d’autres moments, le contexte du projet d’un élément n’est pas explicitement spécifié. Par exemple, le contexte d’un élément n’est pas disponible lorsque l’utilisateur ouvre un fichier en sélectionnant la commande **de fichier existant ouvert** sur le menu Du **fichier,** lorsque le débbuggeur fonctionne sur un fichier, ou lorsque l’utilisateur clique sur la commande **Localiser les fichiers** dans la boîte de dialogue Trouver et **remplacer.** Pour gérer ces situations, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument> l’IDE appelle à gérer le processus de recherche du meilleur projet pour ouvrir un document.

## <a name="see-also"></a>Voir aussi
- [Priorité de projet](../../extensibility/internals/project-priority.md)
- [Ajout d’un projet et de modèles d’élément de projet](../../extensibility/internals/adding-project-and-project-item-templates.md)
