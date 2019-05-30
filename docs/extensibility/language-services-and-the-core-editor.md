---
title: Services de langage et de l’éditeur principal | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - language services
ms.assetid: e03199a6-ad5f-4075-bfba-8d36865112b7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a27fc9ec55b301dc3355e03e2e86e968752fbbd0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66309535"
---
# <a name="language-services-and-the-core-editor"></a>Services de langage et de l’éditeur principal
Éditeurs de Visual Studio sont souvent associés à un service de langage. Entre autres choses, un service de langage fournit la coloration syntaxique, la saisie semi-automatique des instructions, IntelliSense et la mise en forme du texte.

## <a name="core-editors-and-document-data-objects"></a>Éditeurs de Core et des objets de données de document
 Lorsque vous accédez à l’éditeur principal, vous ne créez pas de données de document et les objets de vue de document. L’IDE crée et contrôle de ces deux objets, et vous procurer les handles en effectuant les appels appropriés dans l’éditeur de votre implémentation de la fabrique.

 Pour plus d’informations, consultez [déterminer quel éditeur ouvre un fichier dans un projet](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md).

## <a name="language-services-and-the-core-editor"></a>Services de langage et de l’éditeur principal
 En implémentant un service de langage, vous pouvez contrôler la façon dont les données sont affichées dans la vue de document. Un service de langage fournit des informations et comportement est spécifique à une langue donnée, tels que Visual C++. Lorsque vous créez une mémoire tampon de texte et déterminez l’extension de nom de fichier pour le document que vous ouvrez, la mémoire tampon de texte détermine le service de langage associé à cette extension de nom de fichier à partir d’une clé de Registre **HKEY_LOCAL_MACHINE\SOFTWARE\ Microsoft\Editors\\{GUID YourLanguageService} \Extensions**. Le VSPackage standard chargement procédure puis charge votre VSPackage et une instance de votre service de langage est créée.

 Un service de langage de base est indiqué dans l’illustration suivante.

 ![Graphique de modèle de Service de langage](../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel") objets de service d’éditeur et la langue de base

 L’objet de données de document pour l’éditeur principal est appelé une mémoire tampon de texte et est représenté par le <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objet. L’objet de vue de document est appelée un affichage de texte et est représenté par le <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> objet. Ces deux objets fonctionnent ensemble via le service de langage pour fournir une vue unifiée de l’éditeur principal. Informations à partir de la mémoire tampon de texte et l’affichage de texte présente dans une fenêtre de document appelée une fenêtre de code. Le document de la fenêtre code est géré par un gestionnaire de fenêtre de code.

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>
- <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>
- <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>
- [Fournir un contexte de service de langage à l’aide de l’API héritée](../extensibility/providing-a-language-service-context-by-using-the-legacy-api.md)
- [Hébergement d’IntelliSense](../extensibility/intellisense-hosting.md)
- [Langues de relation contenant-contenus](../extensibility/contained-languages.md)
- [Développer un service de langage hérité](../extensibility/internals/developing-a-legacy-language-service.md)