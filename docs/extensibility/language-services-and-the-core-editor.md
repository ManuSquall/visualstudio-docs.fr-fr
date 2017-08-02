---
title: "Services de langage et de l’éditeur principal | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - language services
ms.assetid: e03199a6-ad5f-4075-bfba-8d36865112b7
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: c78c3c5e450ffe348a8af2687e2b9b30b1128e8e
ms.lasthandoff: 02/22/2017

---
# <a name="language-services-and-the-core-editor"></a>Services de langage et de l’éditeur de base
Éditeurs dans Visual Studio sont souvent associés à un service de langage. Entre autres choses, un service de langage fournit la coloration de syntaxe, la saisie semi-automatique des instructions, IntelliSense et la mise en forme du texte.  
  
## <a name="core-editors-and-document-data-objects"></a>Éditeurs de base et des objets de données de Document  
 Lorsque vous accédez à l’éditeur principal, vous ne créez pas de données de documents et les objets de vue de document. L’IDE crée et contrôle de ces deux objets, et vous procurer les handles en effectuant les appels appropriés dans votre éditeur de mise en œuvre de la fabrique.  
  
 Pour plus d’informations, consultez [déterminer quel éditeur ouvre un fichier dans un projet](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md).  
  
## <a name="language-services-and-the-core-editor"></a>Services de langage et de l’éditeur de base  
 En implémentant un service de langage, vous pouvez contrôler comment les données sont affichées dans la vue de document. Un service de langage fournit des informations et le comportement est spécifique à une langue donnée, tels que Visual C++. Lorsque vous créez une mémoire tampon de texte et déterminez l’extension de nom de fichier pour le document que vous ouvrez, la mémoire tampon de texte détermine le service de langage associé à cette extension de nom de fichier à partir d’une clé de Registre HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Editors\\{GUID YourLanguageService} \Extensions. Le VSPackage standard chargement procédure puis charge votre VSPackage et une instance de votre service de langage est créée.  
  
 Un service de base du langage est indiqué dans l’illustration suivante.  
  
 ![Graphique du modèle de Service de langage](~/extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel")  
Objets de service éditeur et la langue de base  
  
 L’objet de données de document pour l’éditeur de base est appelée mémoire tampon de texte et est représenté par la <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>objet.</xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> L’objet de vue de document est appelée une vue de texte et est représenté par la <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>objet.</xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> Ces deux objets collaborent via le service de langage pour fournir une vue unifiée de l’éditeur principal. Pour plus d’informations à partir de la mémoire tampon de texte et le mode texte s’affiche dans une fenêtre de document appelé une fenêtre de code. Le document de la fenêtre de code est géré par un gestionnaire de fenêtre de code.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo></xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer></xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView></xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager></xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow></xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 [Fournir un contexte de Service de langage à l’aide de l’API héritée](../extensibility/providing-a-language-service-context-by-using-the-legacy-api.md)   
 [Hébergement d’IntelliSense](../extensibility/intellisense-hosting.md)   
 [Langues de relation contenant-contenus](../extensibility/contained-languages.md)   
 [Développement d’un Service de langage hérité](../extensibility/internals/developing-a-legacy-language-service.md)
