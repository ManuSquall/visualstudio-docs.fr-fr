---
title: Validation des points d’arrêt dans un service de langage hérité | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- breakpoint validation
- language services [managed package framework], breakpoint validation
ms.assetid: a7e873cd-dfe1-474f-bda5-fd7532774b15
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f54dc683aa4287145a27e22d49397241b395f69f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68163678"
---
# <a name="validating-breakpoints-in-a-legacy-language-service"></a>Validation des points d’arrêt dans un service de langage hérité
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un point d’arrêt indique que l’exécution du programme doit s’arrêter à un point particulier lorsqu’il est exécuté dans un débogueur. Un utilisateur peut placer un point d’arrêt sur n’importe quelle ligne du fichier source, puisque l’éditeur n’a aucune connaissance de ce qui constitue un emplacement valide pour un point d’arrêt. Quand le débogueur est lancé, tous les points d’arrêt marqués (appelés points d’arrêt en attente) sont liés à l’emplacement approprié dans le programme en cours d’exécution. En même temps, les points d’arrêt sont validés pour s’assurer qu’ils marquent des emplacements de code valides. Par exemple, un point d’arrêt sur un commentaire n’est pas valide, car il n’y a pas de code à cet emplacement dans le code source. Le débogueur désactive les points d’arrêt non valides.  
  
 Étant donné que le service de langage connaît le code source affiché, il peut valider des points d’arrêt avant le lancement du débogueur. Vous pouvez substituer la <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> méthode pour retourner une étendue spécifiant un emplacement valide pour un point d’arrêt. L’emplacement du point d’arrêt est toujours validé lors du lancement du débogueur, mais l’utilisateur est averti des points d’arrêt non valides sans attendre le chargement du débogueur.  
  
## <a name="implementing-support-for-validating-breakpoints"></a>Implémentation de la prise en charge de la validation des points d’arrêt  
  
- La <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> méthode reçoit la position du point d’arrêt. Votre implémentation doit décider si l’emplacement est valide ou non, et l’indiquer en retournant une étendue de texte qui identifie le code associé à la position de ligne du point d’arrêt.  
  
- Retourne <xref:Microsoft.VisualStudio.VSConstants.S_OK> si l’emplacement est valide ou <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> s’il n’est pas valide.  
  
- Si le point d’arrêt est valide, l’étendue de texte est mise en surbrillance avec le point d’arrêt.  
  
- Si le point d’arrêt n’est pas valide, un message d’erreur s’affiche dans la barre d’État.  
  
### <a name="example"></a>Exemple  
 Cet exemple montre une implémentation de la <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> méthode qui appelle l’analyseur pour obtenir l’étendue de code (le cas échéant) à l’emplacement spécifié.  
  
 Cet exemple suppose que vous avez ajouté une `GetCodeSpan` méthode à la <xref:Microsoft.VisualStudio.Package.AuthoringSink> classe qui valide l’étendue de texte et retourne la valeur `true` s’il s’agit d’un emplacement de point d’arrêt valide.  
  
```csharp  
using Microsoft VisualStudio;  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    class TestLanguageService : LanguageService  
    {  
        public override int ValidateBreakpointLocation(IVsTextBuffer buffer,  
                                                       int line,  
                                                       int col,  
                                                       TextSpan[] pCodeSpan)  
        {  
            int retval = VSConstants.S_FALSE;  
            if (pCodeSpan != null)  
            {  
                // Initialize span to current line by default.  
                pCodeSpan[0].iStartLine = line;  
                pCodeSpan[0].iStartIndex = col;  
                pCodeSpan[0].iEndLine = line;  
                pCodeSpan[0].iEndIndex = col;  
            }  
  
            if (buffer != null)  
            {  
                IVsTextLines textLines = buffer as IVsTextLines;  
                if (textLines != null)  
                {  
                    Source src = this.GetSource(textLines);  
                    if (src != null)  
                    {  
                        TokenInfo tokenInfo = new TokenInfo();  
                        string text = src.GetText();  
                        ParseRequest req = CreateParseRequest(src,  
                                                              line,  
                                                              col,  
                                                              tokenInfo,  
                                                              text,  
                                                              src.GetFilePath(),  
                                                              ParseReason.CodeSpan,  
                                                              null);  
                        req.Scope = this.ParseSource(req);  
                        TestAuthoringSink sink = req.Sink as TestAuthoringSink;  
  
                        TextSpan span = new TextSpan();  
                        if (sink.GetCodeSpan(out span))  
                        {  
                            pCodeSpan[0] = span;  
                            retval = VSConstants.S_OK;  
                        }  
                    }  
                }  
            }  
            return retval;  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités du service de langage hérité](../../extensibility/internals/legacy-language-service-features1.md)
