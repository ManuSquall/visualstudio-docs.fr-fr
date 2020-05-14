---
title: Priorité du projet (en anglais seulement) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: 9f707592-2fb6-4f75-9269-f6d4700a998e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a75c1c333d88e1bf5524281bee8b2a683ca6c98e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706421"
---
# <a name="project-priority"></a>Priorité de projet
Un élément de projet est généralement membre d’un seul projet dans la solution. Par conséquent, l’IDE peut facilement déterminer quel projet est utilisé pour ouvrir l’article. Toutefois, si un élément est membre de plus d’un projet, l’IDE utilise un schéma prioritaire pour déterminer le meilleur projet pour l’ouverture de l’article.

 La liste suivante montre le schéma prioritaire du projet :

- L’IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A> appelle la méthode pour chaque projet dans la solution pour déterminer si le document est membre de ce projet.

- Si le document est membre du projet, le projet répond avec une priorité que le projet attribue en fonction de sa gestion de ce document. Par exemple, un projet linguistique répond avec une grande priorité pour ses fichiers de source linguistique, mais répond avec une priorité moindre pour un type de fichier non reconnu qui n’est pas utilisé dans le cadre de son processus de construction.

- Les projets qui fournissent des éditeurs ou des concepteurs personnalisés et spécifiques à un projet pour un document bénéficient également d’une grande priorité.

- L’énumération <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> fournit les valeurs prioritaires du document.

- Le projet qui précise la plus haute priorité est donné le contexte pour ouvrir le document. Si deux projets retournent des valeurs prioritaires égales, le projet actif est préféré. Si aucun projet dans la solution ne répond qu’il peut ouvrir le document, l’IDE met le document dans le projet Divers Files. Pour plus d’informations, voir [Divers Files Project](../../extensibility/internals/miscellaneous-files-project.md).

## <a name="see-also"></a>Voir aussi
- [Projet Fichiers divers](../../extensibility/internals/miscellaneous-files-project.md)
- [Guide pratique pour ouvrir des éditeurs pour les documents ouverts](../../extensibility/how-to-open-editors-for-open-documents.md)
- [Ajout d’un projet et de modèles d’élément de projet](../../extensibility/internals/adding-project-and-project-item-templates.md)
