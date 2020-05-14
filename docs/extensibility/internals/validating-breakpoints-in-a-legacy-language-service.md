---
title: Valider les points d’arrêt dans un service de langue héritée (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoint validation
- language services [managed package framework], breakpoint validation
ms.assetid: a7e873cd-dfe1-474f-bda5-fd7532774b15
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af09e4f8f2156100bea9267c92ffebeb64ce1aa3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704092"
---
# <a name="validating-breakpoints-in-a-legacy-language-service"></a>Validation des points d’arrêt dans un service de langage hérité
Un point d’arrêt indique que l’exécution du programme doit s’arrêter à un moment donné pendant qu’il est exécuté dans un débbugger. Un utilisateur peut placer un point d’arrêt sur n’importe quelle ligne dans le fichier source, puisque l’éditeur n’a aucune connaissance de ce qui constitue un emplacement valide pour un point d’arrêt. Lorsque le débbuggeur est lancé, tous les points d’arrêt marqués (appelés points d’arrêt en attente) sont liés à l’emplacement approprié dans le programme de course. Dans le même temps, les points d’arrêt sont validés pour s’assurer qu’ils marquent des emplacements de code valides. Par exemple, un point d’arrêt sur un commentaire n’est pas valide, car il n’y a pas de code à cet endroit dans le code source. Le débagé debugger désactive les points d’arrêt invalides.

 Étant donné que le service linguistique connaît le code source affiché, il peut valider les points d’arrêt avant le lancement du débbuggeur. Vous pouvez remplacer <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> la méthode pour retourner une portée spécifiant un emplacement valide pour un point d’arrêt. L’emplacement du point d’arrêt est toujours validé lorsque le débbuggeur est lancé, mais l’utilisateur est informé des points de rupture invalides sans attendre que le débbuggeur se charge.

## <a name="implementing-support-for-validating-breakpoints"></a>Mise en œuvre d’un soutien pour valider les points d’arrêt

- La <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> méthode est donnée la position du point d’arrêt. Votre implémentation doit décider si l’emplacement est valide ou non, et l’indiquer en retournant une travée de texte qui identifie le code associé à la position de ligne le point d’arrêt.

- Retournez <xref:Microsoft.VisualStudio.VSConstants.S_OK> si l’emplacement <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> est valide ou s’il n’est pas valide.

- Si le point d’arrêt est valide, la durée du texte est mise en surbrillance avec le point d’arrêt.

- Si le point d’arrêt est invalide, un message d’erreur apparaît dans la barre d’état.

### <a name="example"></a>Exemple
 Cet exemple montre une <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> mise en œuvre de la méthode qui appelle le analyseur pour obtenir la durée du code (le cas échéant) à l’emplacement spécifié.

 Cet exemple suppose que vous `GetCodeSpan` avez <xref:Microsoft.VisualStudio.Package.AuthoringSink> ajouté une méthode à la `true` classe qui valide la durée de texte et renvoie s’il s’agit d’un emplacement de point d’arrêt valide.

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
- [Fonctionnalités du service de langage hérité](../../extensibility/internals/legacy-language-service-features1.md)
