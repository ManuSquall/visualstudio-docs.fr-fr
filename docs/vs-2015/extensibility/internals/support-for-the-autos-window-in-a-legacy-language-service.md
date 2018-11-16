---
title: Prise en charge de la fenêtre automatique dans un Service de langage hérité | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- language services [managed package framework], Autos window
- Autos window, supporting in language services [managed package framework]
ms.assetid: 47d40aae-7a3c-41e1-a949-34989924aefb
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8e1f787b3a0f2ab1c153dfd3742c8939975e3ad1
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51764474"
---
# <a name="support-for-the-autos-window-in-a-legacy-language-service"></a>Prise en charge de Fenêtre Automatique dans un service de langage hérité
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Le **automatique** fenêtre affiche des expressions telles que des variables et des paramètres qui sont dans la portée lorsque le programme débogué est suspendu (soit en raison d’un point d’arrêt ou une exception). Les expressions peuvent inclure des variables, locales ou globales et les paramètres qui ont été modifiés dans la portée locale. Le **automatique** fenêtre peut également inclure des instanciations d’une classe, structure ou un autre type. Quoi que ce soit un évaluateur d’expression peut évaluer peut potentiellement être affiché dans le **automatique** fenêtre.  
  
 L’infrastructure de package managé (MPF) ne fournit pas de prise en charge directe pour les **automatique** fenêtre. Toutefois, si vous remplacez le <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> (méthode), vous pouvez retourner une liste d’expressions pour être présenté dans le **automatique** fenêtre.  
  
## <a name="implementing-support-for-the-autos-window"></a>Implémentation de prise en charge de la fenêtre automatique  
 Il vous suffit pour prendre en charge la **automatique** fenêtre consiste à implémenter la <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> méthode dans la <xref:Microsoft.VisualStudio.Package.LanguageService> classe. Votre implémentation doit décider, étant donné un emplacement dans le fichier source, les expressions devant apparaître dans le **automatique** fenêtre. La méthode retourne une liste de chaînes dans lequel chaque chaîne représente une expression unique. La valeur de retour <xref:Microsoft.VisualStudio.VSConstants.S_OK> indique que la liste contient des expressions, tandis que <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> indique qu’il n’y a aucune expression à afficher.  
  
 Les expressions réelles retournées sont les noms des variables ou paramètres qui s’affichent à cet emplacement dans le code. Ces noms sont transmis à l’évaluateur d’expression pour obtenir les valeurs et les types qui sont ensuite affichées dans le **automatique** fenêtre.  
  
### <a name="example"></a>Exemple  
 L’exemple suivant illustre une implémentation de la <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> méthode qui obtient une liste d’expressions à partir de la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode à l’aide de la raison de l’analyse <xref:Microsoft.VisualStudio.Package.ParseReason>. Chacune des expressions est encapsulé comme un `TestVsEnumBSTR` qui implémente le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsEnumBSTR> interface.  
  
 Notez que le `GetAutoExpressionsCount` et `GetAutoExpression` méthodes sont des méthodes personnalisées sur le `TestAuthoringSink` de l’objet et ont été ajoutées pour prendre en charge de cet exemple. Ils représentent un moyen dans les expressions ajoutées à la `TestAuthoringSink` objet par l’analyseur (en appelant le <xref:Microsoft.VisualStudio.Package.AuthoringSink.AutoExpression%2A> méthode) sont accessibles en dehors de l’analyseur.  
  
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

