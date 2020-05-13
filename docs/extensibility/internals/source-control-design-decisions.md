---
title: Décisions de conception de contrôle des sources (en anglais) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], design decisions
ms.assetid: 5f60ec1a-5a74-4362-8293-817a4dd73872
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c36bb2b50a72a52aeaeb7712f4ed711845b5e6d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705255"
---
# <a name="source-control-design-decisions"></a>Décisions de conception du contrôle de code source
Les décisions de conception suivantes doivent être prises en considération pour les projets lors de la mise en œuvre du contrôle des sources.

## <a name="will-information-be-shared-or-private"></a>L’information sera-t-elle partagée ou privée?
 La décision de conception la plus importante que vous pouvez prendre est ce que l’information est sharable et ce qui est privé. Par exemple, la liste des fichiers pour le projet est partagée, mais dans cette liste de fichiers, certains utilisateurs peuvent vouloir avoir des fichiers privés. Les paramètres de compilateur sont partagés, mais le projet de démarrage est généralement privé. Les paramètres sont soit purement partagés, partagés avec un remplacement, soit purement privés. Par conception, les articles privés, tels que les fichiers d’options utilisateur Solution (.suo), ne sont pas enregistrés [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]dans . Assurez-vous de stocker des informations privées dans des fichiers privés tels que le fichier .suo, ou un fichier privé spécifique que vous créez, par exemple, un fichier .csproj.user pour Visual C ou un fichier .vbproj.user pour Visual Basic.

 Cette décision n’est pas exhaustive et peut être prise point par point.

## <a name="will-the-project-include-special-files"></a>Le projet comprendra-t-il des dossiers spéciaux?
 Une autre décision importante de conception est de savoir si votre structure de projet utilise des fichiers spéciaux. Les fichiers spéciaux sont des fichiers cachés qui sous-tendent les fichiers qui sont visibles dans Solution Explorer et dans les cases de dialogue d’enregistrement et de check-out. Si vous utilisez des fichiers spéciaux, suivez ces lignes directrices :

1. N’associez pas les fichiers spéciaux au nœud racine du projet, c’est-à-dire au dossier du projet lui-même. Votre dossier de projet doit être un seul fichier.

2. Lorsque des fichiers spéciaux sont ajoutés, supprimés <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> ou renommés dans un projet, les événements appropriés doivent être déclenchés avec l’ensemble de drapeau qui indique que les fichiers sont des fichiers spéciaux. Ces événements sont appelés par l’environnement en <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> réponse au projet appelant les méthodes appropriées.

3. Lorsque votre projet <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> ou votre éditeur demande un fichier, les fichiers spéciaux associés à ce fichier ne sont pas automatiquement vérifiés. Passez les fichiers spéciaux avec le fichier parent. L’environnement détectera la relation entre tous les fichiers qui sont transmis et cachera de manière appropriée les fichiers spéciaux dans l’interface utilisateur de départ.

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- [Prise en charge du contrôle de code source](../../extensibility/internals/supporting-source-control.md)
