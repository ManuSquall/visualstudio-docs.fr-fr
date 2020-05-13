---
title: Prise en charge de la fenêtre Autos dans un service de langue héritée (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], Autos window
- Autos window, supporting in language services [managed package framework]
ms.assetid: 47d40aae-7a3c-41e1-a949-34989924aefb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 75f8c761721dde5dad4bb75b8675f71f678b06df
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704880"
---
# <a name="support-for-the-autos-window-in-a-legacy-language-service"></a>Prise en charge de Fenêtre Automatique dans un service de langage hérité
La fenêtre **Autos** affiche des expressions telles que des variables et des paramètres qui sont de portée lorsque le programme en cours de débbugged est mis en pause (soit en raison d’un point d’arrêt ou d’une exception). Les expressions peuvent inclure des variables, locales ou mondiales, et des paramètres qui ont été modifiés dans la portée locale. La fenêtre **Autos** peut également inclure des instantanés d’une classe, d’une structure ou d’un autre type. Tout ce qu’un évaluateur d’expression peut évaluer peut potentiellement être montré dans la fenêtre **Autos.**

 Le cadre de paquet géré (MPF) ne fournit pas de support direct pour la fenêtre **Autos.** Toutefois, si vous <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> remplacez la méthode, vous pouvez retourner une liste d’expressions à présenter dans la fenêtre **Autos.**

## <a name="implementing-support-for-the-autos-window"></a>Mise en œuvre du support pour la fenêtre Autos
 Tout ce que vous devez faire pour soutenir <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> la <xref:Microsoft.VisualStudio.Package.LanguageService> fenêtre **Autos** est de mettre en œuvre la méthode dans la classe. Votre implémentation doit décider, compte tenu d’un emplacement dans le fichier source, quelles expressions doivent apparaître dans la fenêtre **Autos.** La méthode renvoie une liste de chaînes dans lesquelles chaque chaîne représente une seule expression. Une valeur <xref:Microsoft.VisualStudio.VSConstants.S_OK> de retour indique que <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> la liste contient des expressions, tout en indiquant qu’il n’y a pas d’expressions à montrer.

 Les expressions réelles retournées sont les noms des variables ou des paramètres qui apparaissent à cet endroit dans le code. Ces noms sont transmis à l’évaluateur d’expression pour obtenir des valeurs et des types qui sont ensuite affichés dans la fenêtre **Autos.**

### <a name="example"></a>Exemple
 L’exemple suivant montre <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> une mise en œuvre <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> de la méthode <xref:Microsoft.VisualStudio.Package.ParseReason>qui obtient une liste d’expressions de la méthode en utilisant la raison d’analyse . Chacune des expressions est `TestVsEnumBSTR` enveloppée <xref:Microsoft.VisualStudio.TextManager.Interop.IVsEnumBSTR> comme un qui implémente l’interface.

 Notez `GetAutoExpressionsCount` que `GetAutoExpression` les méthodes et `TestAuthoringSink` les méthodes sont des méthodes personnalisées sur l’objet et ont été ajoutés à l’appui de cet exemple. Ils représentent une façon dont `TestAuthoringSink` les expressions ajoutées à l’objet par l’analyseur (en appelant la <xref:Microsoft.VisualStudio.Package.AuthoringSink.AutoExpression%2A> méthode) peuvent être consultées en dehors du parseur.

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
