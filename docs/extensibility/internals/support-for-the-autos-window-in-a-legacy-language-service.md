---
title: Prendre en charge la fenêtre automatique dans un service de langage hérité
description: Découvrez comment implémenter la prise en charge de la fenêtre automatique, qui affiche les expressions qui se trouvent dans la portée lorsque le programme en cours de débogage est suspendu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], Autos window
- Autos window, supporting in language services [managed package framework]
ms.assetid: 47d40aae-7a3c-41e1-a949-34989924aefb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b0d02107e8f0128e7a91f679eb8c651515e39ace
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969902"
---
# <a name="support-for-the-autos-window-in-a-legacy-language-service"></a>Prise en charge de la fenêtre automatique dans un service de langage hérité

La fenêtre **automatique** affiche des expressions telles que les variables et les paramètres qui se trouvent dans la portée lorsque le programme en cours de débogage est suspendu (en raison d’un point d’arrêt ou d’une exception). Les expressions peuvent inclure des variables, des paramètres locaux ou globaux et des paramètres qui ont été modifiés dans l’étendue locale. La fenêtre **automatique** peut également inclure des instanciations d’une classe, d’une structure ou d’un autre type. Tout ce qu’un évaluateur d’expression peut évaluer peut éventuellement s’afficher dans la fenêtre **automatique** .

 Managed package Framework (MPF) ne fournit pas de prise en charge directe pour la fenêtre **automatique** . Toutefois, si vous substituez la <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> méthode, vous pouvez retourner une liste d’expressions à présenter dans la fenêtre **automatique** .

## <a name="implementing-support-for-the-autos-window"></a>Implémentation de la prise en charge de la fenêtre automatique

 Pour prendre en charge la fenêtre **automatique** , il vous suffit d’implémenter la <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> méthode dans la <xref:Microsoft.VisualStudio.Package.LanguageService> classe. Votre implémentation doit décider, étant donné un emplacement dans le fichier source, les expressions qui doivent apparaître dans la fenêtre **automatique** . La méthode retourne une liste de chaînes dans laquelle chaque chaîne représente une expression unique. La valeur de retour <xref:Microsoft.VisualStudio.VSConstants.S_OK> indique que la liste contient des expressions, tandis que <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> indique qu’il n’y a pas d’expressions à afficher.

 Les expressions réelles retournées sont les noms des variables ou des paramètres qui s’affichent à cet emplacement dans le code. Ces noms sont passés à l’évaluateur d’expression pour obtenir des valeurs et des types qui sont ensuite affichés dans la fenêtre **automatique** .

### <a name="example"></a>Exemple
 L’exemple suivant illustre une implémentation de la <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> méthode qui obtient une liste d’expressions à partir de la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode à l’aide de la raison de l’analyse <xref:Microsoft.VisualStudio.Package.ParseReason> . Chacune des expressions est encapsulée sous la forme d’un `TestVsEnumBSTR` qui implémente l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsEnumBSTR> interface.

 Notez que les `GetAutoExpressionsCount` `GetAutoExpression` méthodes et sont des méthodes personnalisées sur l' `TestAuthoringSink` objet et ont été ajoutées pour prendre en charge cet exemple. Ils représentent une façon dont les expressions ajoutées à l' `TestAuthoringSink` objet par l’analyseur (en appelant la <xref:Microsoft.VisualStudio.Package.AuthoringSink.AutoExpression%2A> méthode) sont accessibles à l’extérieur de l’analyseur.

```csharp
using Microsoft.VisualStudio;
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        public override int GetProximityExpressions(IVsTextBuffer buffer,
                                                    int line,
                                                    int col,
                                                    int cLines,
                                                    out IVsEnumBSTR ppEnum)
        {
            int retval = VSConstants.E_NOTIMPL;
            ppEnum = null;
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
                                                              ParseReason.Autos,
                                                              null);
                        req.Scope = this.ParseSource(req);
                        TestAuthoringSink sink = req.Sink as TestAuthoringSink;

                        retval = VSConstants.S_FALSE;
                        int spanCount = sink.GetAutoExpressionsCount();
                        if (spanCount > 0) {
                            TestVsEnumBSTR bstrList = new TestVsEnumBSTR();
                            for (int i = 0; i < spanCount; i++)
                            {
                                TextSpan span;
                                sink.GetAutoExpression(i, out span);
                                string expression = src.GetText(span.iStartLine,
                                                                span.iStartIndex,
                                                                span.iEndLine,
                                                                span.iEndIndex);
                                bstrList.AddString(expression);
                            }
                            ppEnum = bstrList;
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
