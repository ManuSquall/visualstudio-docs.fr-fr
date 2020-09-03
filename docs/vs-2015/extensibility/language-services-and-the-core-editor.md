---
title: Services de langage et éditeur principal | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - language services
ms.assetid: e03199a6-ad5f-4075-bfba-8d36865112b7
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1e708ffe796bfc9342bc20c3e7f20d5cf0d05058
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180302"
---
# <a name="language-services-and-the-core-editor"></a>Services linguistiques et éditeur de base
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans Visual Studio, les éditeurs sont fréquemment associés à un service de langage. Entre autres choses, un service de langage fournit la coloration syntaxique, la saisie semi-automatique des instructions, IntelliSense et la mise en forme du texte.  
  
## <a name="core-editors-and-document-data-objects"></a>Éditeurs de base et objets de données de document  
 Lorsque vous accédez à l’éditeur principal, vous ne créez pas de données de document ni d’objets de vue de document. L’IDE crée et contrôle ces deux objets et vous leur obtenez des handles en effectuant les appels appropriés dans votre implémentation de fabrique d’éditeur.  
  
 Pour plus d’informations, consultez [détermination de l’éditeur qui ouvre un fichier dans un projet](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md).  
  
## <a name="language-services-and-the-core-editor"></a>Services linguistiques et éditeur de base  
 En implémentant un service de langage, vous pouvez contrôler la façon dont les données sont affichées dans la vue de document. Un service de langage fournit des informations et un comportement spécifiques à un langage donné, par exemple Visual C++. Lorsque vous créez une mémoire tampon de texte et déterminez l’extension de nom de fichier du document que vous ouvrez, la mémoire tampon de texte détermine le service de langage associé à cette extension de nom de fichier à partir d’une clé de Registre, HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Editors \\ {YOURLANGUAGESERVICE GUID} \Extensions. La procédure de chargement du VSPackage standard charge ensuite votre VSPackage et une instance de votre service de langage est créée.  
  
 Un service de langage de base est présenté dans l’illustration suivante.  
  
 ![Graphique du modèle de service de langage](../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel")  
Éditeur principal et objets de service de langage  
  
 L’objet de données de document pour l’éditeur de base est appelé une mémoire tampon de texte et est représenté par l' <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objet. L’objet de vue de document est appelé un affichage de texte et est représenté par l' <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> objet. Ces deux objets fonctionnent ensemble par le biais du service de langage pour fournir une vue unifiée de l’éditeur principal. Les informations de la mémoire tampon de texte et de la vue de texte s’affichent dans une fenêtre de document appelée fenêtre de code. Le document de la fenêtre de code est géré par un gestionnaire de fenêtre de code.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 [Fourniture d’un contexte de service de langage à l’aide de l’API héritée](../extensibility/providing-a-language-service-context-by-using-the-legacy-api.md)   
 [Hébergement IntelliSense](../extensibility/intellisense-hosting.md)   
 [Langues contenues](../extensibility/contained-languages.md)   
 [Développement d’un service de langage hérité](../extensibility/internals/developing-a-legacy-language-service.md)
