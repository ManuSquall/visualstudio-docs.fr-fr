---
title: Services de langage et de l’éditeur principal | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - language services
ms.assetid: e03199a6-ad5f-4075-bfba-8d36865112b7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cd9e0cdbcb10ac670ac1a0947fb9a43c16c7fccf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="language-services-and-the-core-editor"></a>Services de langage et de l’éditeur principal
Les éditeurs dans Visual Studio sont souvent associés à un service de langage. Entre autres choses, un service de langage fournit la coloration de syntaxe, la saisie semi-automatique des instructions, IntelliSense et la mise en forme du texte.  
  
## <a name="core-editors-and-document-data-objects"></a>Éditeurs de noyaux et les objets de données de Document  
 Lorsque vous accédez à l’éditeur principal, vous ne créez pas de données du document et les objets de vue de document. L’IDE crée et contrôle de ces deux objets, et vous procurer les handles en effectuant les appels appropriés dans l’éditeur de votre implémentation de la fabrique.  
  
 Pour plus d’informations, consultez [détermination de l’éditeur ouvre un fichier dans un projet](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md).  
  
## <a name="language-services-and-the-core-editor"></a>Services de langage et de l’éditeur principal  
 En implémentant un service de langage, vous pouvez contrôler la façon dont les données sont affichées dans l’affichage du document. Un service de langage fournit des informations et comportement qui est spécifique à une langue donnée, tels que Visual C++. Lorsque vous créez une mémoire tampon de texte et déterminez l’extension de nom de fichier pour le document que vous ouvrez, la mémoire tampon de texte détermine le service de langage associé à cette extension de nom de fichier à partir d’une clé de Registre HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Editors \\{GUID YourLanguageService} \Extensions. Le VSPackage standard chargement procédure puis charge votre VSPackage et une instance de votre service de langage est créée.  
  
 Un service de langage de base est indiqué dans l’illustration suivante.  
  
 ![Graphique de modèle de Service de langage](../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel")  
Objets de service éditeur et la langue de base  
  
 L’objet de données de document pour l’éditeur de base est appelée mémoire tampon de texte et est représenté par la <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objet. L’objet de vue de document est appelée une vue de texte et est représenté par la <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> objet. Ces deux objets fonctionnent ensemble via le service de langage pour fournir une vue unifiée de l’éditeur principal. Pour plus d’informations à partir de la mémoire tampon de texte et le mode texte s’affiche dans une fenêtre de document appelé une fenêtre de code. Le document de la fenêtre code est géré par un gestionnaire de fenêtre de code.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 [Fournissant un contexte de Service de langage à l’aide de l’API héritée](../extensibility/providing-a-language-service-context-by-using-the-legacy-api.md)   
 [Hébergement d’IntelliSense](../extensibility/intellisense-hosting.md)   
 [Langues de relation contenant-contenus](../extensibility/contained-languages.md)   
 [Développement d’un service de langage hérité](../extensibility/internals/developing-a-legacy-language-service.md)