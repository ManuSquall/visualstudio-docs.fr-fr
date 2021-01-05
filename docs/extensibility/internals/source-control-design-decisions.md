---
title: Décisions relatives à la conception du contrôle de code source | Microsoft Docs
description: Découvrez plusieurs décisions de conception clés à prendre en compte pour les projets lors de l’implémentation du contrôle de code source.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 98e84167bc9cbbcad41b897c2de69115c6827ca5
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97875516"
---
# <a name="source-control-design-decisions"></a>Décisions de conception du contrôle de code source
Les décisions de conception suivantes doivent être prises en compte pour les projets lors de l’implémentation du contrôle de code source.

## <a name="will-information-be-shared-or-private"></a>Les informations seront-elles partagées ou privées ?
 La décision la plus importante en matière de conception consiste à savoir quelles informations peuvent être partagées et ce qui est privé. Par exemple, la liste des fichiers du projet est partagée, mais dans cette liste de fichiers, certains utilisateurs peuvent souhaiter avoir des fichiers privés. Les paramètres du compilateur sont partagés, mais le projet de démarrage est généralement privé. Les paramètres sont soit entièrement partagés, partagés avec un remplacement, soit purement privés. Par défaut, les éléments privés, tels que les fichiers d’options utilisateur de solution (. suo), ne sont pas archivés [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] . Veillez à stocker les informations privées dans des fichiers privés tels que le fichier. suo ou un fichier privé spécifique que vous créez, par exemple, un fichier. csproj. User pour Visual C# ou un fichier. vbproj. User pour Visual Basic.

 Cette décision n’est pas exhaustive et peut être faite sur une base élément par élément.

## <a name="will-the-project-include-special-files"></a>Le projet inclura-t-il des fichiers spéciaux ?
 Une autre décision de conception importante est que la structure de votre projet utilise des fichiers spéciaux. Les fichiers spéciaux sont des fichiers cachés qui sous-tendent les fichiers qui sont visibles dans Explorateur de solutions et dans les boîtes de dialogue d’archivage et d’extraction. Si vous utilisez des fichiers spéciaux, suivez ces instructions :

1. N’associez pas de fichiers spéciaux au nœud racine du projet, c’est-à-dire au fichier projet lui-même. Votre fichier projet doit être un fichier unique.

2. Quand des fichiers spéciaux sont ajoutés, supprimés ou renommés dans un projet, les <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> événements appropriés doivent être déclenchés avec l’indicateur défini qui indique que les fichiers sont des fichiers spéciaux. Ces événements sont appelés par l’environnement en réponse au projet appelant les méthodes appropriées <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> .

3. Lorsque votre projet ou éditeur appelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> un fichier, les fichiers spéciaux associés à ce fichier ne sont pas extraits automatiquement. Transmettez les fichiers spéciaux en même temps que le fichier parent. L’environnement détecte la relation entre tous les fichiers qui sont transmis et masque de manière appropriée les fichiers spéciaux dans l’interface utilisateur de l’extraction.

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- [Prise en charge du contrôle de code source](../../extensibility/internals/supporting-source-control.md)
