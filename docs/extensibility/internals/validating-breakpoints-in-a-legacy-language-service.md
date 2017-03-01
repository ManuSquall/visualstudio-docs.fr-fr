---
title: "Validation des points d’arrêt dans un Service de langage hérité | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- breakpoint validation
- language services [managed package framework], breakpoint validation
ms.assetid: a7e873cd-dfe1-474f-bda5-fd7532774b15
caps.latest.revision: 14
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
ms.openlocfilehash: 3a8c2df45c0a834430a499cf6a7e7ef2da10bdbf
ms.lasthandoff: 02/22/2017

---
# <a name="validating-breakpoints-in-a-legacy-language-service"></a>Validation des points d’arrêt dans un Service de langage hérité
Un point d’arrêt indique que l’exécution du programme doit s’arrêter à un moment donné pendant l’exécution dans un débogueur. Un utilisateur peut placer un point d’arrêt sur n’importe quelle ligne dans le fichier source, comme l’éditeur n’a aucune connaissance de ce qui constitue un emplacement valide pour un point d’arrêt. Lorsque le débogueur est lancé, tous les points d’arrêt marquées (appelés en attente de points d’arrêt) sont liés à l’emplacement approprié dans le programme en cours d’exécution. En même temps que les points d’arrêt sont validées pour garantir qu’ils marquent les emplacements de code valide. Par exemple, un point d’arrêt sur un commentaire n’est pas valide, car il n’existe aucun code à cet emplacement dans le code source. Le débogueur désactive les points d’arrêt non valides.  
  
 Étant donné que le service de langage connaît le code source s’affiche, il peut valider des points d’arrêt avant de lancer le débogueur. Vous pouvez remplacer le <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A>méthode pour retourner une plage en spécifiant un emplacement valide pour un point d’arrêt.</xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> L’emplacement du point d’arrêt est toujours validé lorsque le débogueur est lancé, mais l’utilisateur est averti de points d’arrêt non valides sans attendre que le débogueur charge.  
  
## <a name="implementing-support-for-validating-breakpoints"></a>L’implémentation de la prise en charge pour la validation des points d’arrêt  
  
-   Le <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A>la position du point d’arrêt est donnée à la méthode.</xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> Votre implémentation doit décider ou non de l’emplacement est valide et indiquer ceci en retournant une étendue de texte qui identifie le code associé à la position de ligne du point d’arrêt.  
  
-   Retourner <xref:Microsoft.VisualStudio.VSConstants.S_OK>Si l’emplacement est valide, ou <xref:Microsoft.VisualStudio.VSConstants.S_FALSE>s’il n’est pas valide.</xref:Microsoft.VisualStudio.VSConstants.S_FALSE> </xref:Microsoft.VisualStudio.VSConstants.S_OK>  
  
-   Si le point d’arrêt est valide, l’étendue de texte est mis en surbrillance, ainsi que le point d’arrêt.  
  
-   Si le point d’arrêt n’est pas valide, un message d’erreur s’affiche dans la barre d’état.  
  
### <a name="example"></a>Exemple  
 Cet exemple illustre une implémentation de la <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A>méthode qui appelle l’analyseur pour obtenir l’étendue de code (le cas échéant) à l’emplacement spécifié.</xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A>  
  
 Cet exemple suppose que vous avez ajouté un `GetCodeSpan` méthode à la <xref:Microsoft.VisualStudio.Package.AuthoringSink>classe qui valide l’étendue de texte et la retourne `true` s’il s’agit d’un point d’arrêt valide.</xref:Microsoft.VisualStudio.Package.AuthoringSink>  
  
```c#  
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
 [Fonctionnalités du Service de langage ancien](../../extensibility/internals/legacy-language-service-features1.md)
