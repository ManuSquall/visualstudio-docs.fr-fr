---
title: "Le reformatage du Code dans un Service de langage hérité | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- reformatting code, supporting in language services [managed package framework]
- language services [managed package framework], reformatting code
ms.assetid: 08bb3375-8fef-4f4e-9efa-0d7333bab0eb
caps.latest.revision: 12
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
ms.sourcegitcommit: 08d537f003279283509913d5f3d6aaa1bb1c4600
ms.openlocfilehash: d78fb976b3500a657d080634c6a041c218c3f1a1
ms.lasthandoff: 02/22/2017

---
# <a name="reformatting-code-in-a-legacy-language-service"></a>Le reformatage du Code dans un Service de langage hérité

Dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] code source peut être remis en forme en normalisant l’utilisation des retraits et les espaces blancs. Cela peut inclure insertion ou suppression des espaces ou des tabulations au début de chaque ligne, en ajoutant de nouvelles lignes entre les lignes ou remplaçant les espaces par des tabulations ou les tabulations par des espaces.  
  
>**Remarque :** insertion ou suppression des caractères de saut de ligne peut affecter les marqueurs tels que des points d’arrêt et des signets, mais ajout ou la suppression des espaces ou des tabulations n’affecte pas les marqueurs.  
  
Les utilisateurs peuvent démarrer une opération de reformatage en sélectionnant **la sélection du Format** ou **Document au Format** à partir de la **avancé** menu sur le **modifier** menu. Une opération de reformatage peut également être déclenchée lorsqu’un extrait de code ou un caractère particulier est inséré. Par exemple, lorsque vous tapez une accolade fermante en c#, tout le contenu entre l’accolade ouvrante correspondante et l’accolade fermante est automatiquement mis en retrait correctement.
  
Lors de la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] envoie le **la sélection du Format** ou **Document au Format** commande au service de langage, <xref:Microsoft.VisualStudio.Package.ViewFilter>classe appelle la <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>méthode dans la <xref:Microsoft.VisualStudio.Package.Source>classe.</xref:Microsoft.VisualStudio.Package.Source> </xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> </xref:Microsoft.VisualStudio.Package.ViewFilter> Pour prendre en charge la mise en forme que vous devez substituer la <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>méthode et fournissez votre propre mise en forme du code.</xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>  
  
## <a name="enabling-support-for-reformatting"></a>L’activation de la prise en charge pour la remise en forme  

Pour prendre en charge la mise en forme, les `EnableFormatSelection` paramètre de la <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>doit être défini sur `true` lorsque vous enregistrez votre VSPackage.</xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> Cela définit le <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableFormatSelection%2A>propriété `true`.</xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableFormatSelection%2A> Le <xref:Microsoft.VisualStudio.Package.ViewFilter.CanReformat%2A>méthode retourne la valeur de cette propriété.</xref:Microsoft.VisualStudio.Package.ViewFilter.CanReformat%2A> Si elle retourne la valeur true, <xref:Microsoft.VisualStudio.Package.ViewFilter>classe appelle le <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>.</xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> </xref:Microsoft.VisualStudio.Package.ViewFilter>  
  
## <a name="implementing-reformatting"></a>L’implémentation de reformatage

Pour implémenter le reformatage, vous devez dériver une classe à partir de la <xref:Microsoft.VisualStudio.Package.Source>classe et substituer les <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>méthode.</xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> </xref:Microsoft.VisualStudio.Package.Source> L' <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan>objet décrit l’étendue pour le format et l' <xref:Microsoft.VisualStudio.Package.EditArray>objet contient les modifications apportées sur l’intervalle</xref:Microsoft.VisualStudio.Package.EditArray> </xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> Notez que cette étendue peut être le document entier. Toutefois, dans la mesure où il existe probablement plusieurs modifications sont apportées à l’étendue, toutes les modifications doivent être réversibles en une seule action. Pour ce faire, encapsulez toutes les modifications dans un <xref:Microsoft.VisualStudio.Package.CompoundAction>de l’objet (voir la section de « À l’aide de la classe CompoundAction » dans cette rubrique).</xref:Microsoft.VisualStudio.Package.CompoundAction>

### <a name="example"></a>Exemple  

L’exemple suivant vérifie la qu'existe un espace après chaque virgule dans la sélection, à moins que la virgule est suivie par une tabulation ou à la fin de la ligne. Les espaces de fin après la dernière virgule dans une ligne sont supprimés. Consultez la section « Utilisation de la classe CompoundAction » dans cette rubrique pour voir comment cette méthode est appelée à partir de la <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>méthode.</xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>  

```csharp 
using Microsoft.VisualStudio.Package;  
using Microsoft VisualStudio.TextManager.Interop;  
  
namespace MyLanguagePackage  
{  
    class MySource : Source  
    {  
        private void DoFormatting(EditArray mgr, TextSpan span)  
        {  
            // Make sure there is one space after every comma unless followed  
            // by a tab or comma is at end of line.  
            IVsTextLines pBuffer = GetTextLines();  
            if (pBuffer != null)  
            {  
                int    startIndex = span.iStartIndex;  
                int    endIndex   = 0;  
                string line       = "";  
                // Loop over all lines in span  
                for (int i = span.iStartLine; i <= span.iEndLine; i++)  
                {  
                    if (i < span.iEndLine)  
                    {  
                        pBuffer.GetLengthOfLine(i, out endIndex);  
                    }  
                    else  
                    {  
                        endIndex = span.iEndIndex;  
                    }  
                    pBuffer.GetLineText(i, startIndex, i, endIndex, out line);  
  
                    if (line.Length > 0)  
                    {  
                        int index = 0;  
                        // Loop over all commas in line  
                        while ((index = line.IndexOf(',', index)) != -1)  
                        {  
                            int spaceIndex = index + 1;  
                            // Determine how many spaces after comma  
                            while (spaceIndex < line.Length && line[spaceIndex] == ' ')  
                            {  
                                ++spaceIndex;  
                            }  
  
                            int      spaceCount      = spaceIndex - (index + 1);  
                            string   replacementText = " ";  
                            bool     fDoEdit         = true;  
                            TextSpan editTextSpan    = new TextSpan();  
  
                            editTextSpan.iStartLine  = i;  
                            editTextSpan.iEndLine    = i;  
                            editTextSpan.iStartIndex = index + 1;  
  
                            if (spaceIndex == line.Length)  
                            {  
                                if (spaceCount > 0)  
                                {  
                                    // Delete spaces after a comma at end of line  
                                    editTextSpan.iEndIndex = spaceIndex;  
                                    replacementText = "";  
                                }  
                                else  
                                {  
                                    // Otherwise, do not add spaces if comma is  
                                    // at end of line.  
                                    fDoEdit = false;  
                                }  
                            }  
                            else if (spaceCount == 0)  
                            {  
                                if (spaceIndex < line.Length && line[spaceIndex] == '\t')  
                                {  
                                    // Do not insert space if a tab follows  
                                    // a comma.  
                                    fDoEdit = false;  
                                }  
                                else  
                                {  
                                    // No space after comma so add a space.  
                                    editTextSpan.iEndIndex = index + 1;  
                                }  
                            }  
                            else if (spaceCount > 1)  
                            {  
                                // More than one space after comma, replace  
                                // with a single space.  
                                editTextSpan.iEndIndex = spaceIndex;  
                            }  
                            else  
                            {  
                                // Single space after a comma and not at end  
                                // of the line, leave it alone.  
                                fDoEdit = false;  
                            }  
                            if (fDoEdit)  
                            {  
                                // Add edit operation  
                                mgr.Add(new EditSpan(editTextSpan, replacementText));  
                            }  
                            index = spaceIndex;  
                        }  
                    }  
                    startIndex = 0; // All subsequent lines start at 0  
                }  
                // Apply all edits  
                mgr.ApplyEdits();  
            }  
        }  
    }  
}  
```  
  
## <a name="using-the-compoundaction-class"></a>À l’aide de la classe CompoundAction  
 
Tout le reformatage effectuée sur une section de code doit être réversible en une seule action. Cela peut être accompli à l’aide d’une <xref:Microsoft.VisualStudio.Package.CompoundAction>classe.</xref:Microsoft.VisualStudio.Package.CompoundAction> Cette classe encapsule un ensemble d’opérations de modification de la mémoire tampon de texte dans une opération de modification unique.  
  
### <a name="example"></a>Exemple

Voici un exemple d’utilisation de la <xref:Microsoft.VisualStudio.Package.CompoundAction>classe.</xref:Microsoft.VisualStudio.Package.CompoundAction> Consultez l’exemple dans la section « Mise en œuvre prise en charge pour la mise en forme » dans cette rubrique pour obtenir un exemple de la `DoFormatting` méthode.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft VisualStudio.TextManager.Interop;  
  
namespace MyLanguagePackage  
{  
    class MySource : Source  
    {  
        public override void ReformatSpan(EditArray mgr, TextSpan span)  
        {  
            string description = "Reformat code";  
            CompoundAction ca = new CompoundAction(this, description);  
            using (ca)  
            {  
                ca.FlushEditActions();      // Flush any pending edits  
                DoFormatting(mgr, span);    // Format the span  
            }  
        }  
    }  
}  
```  

## <a name="see-also"></a>Voir aussi

[Fonctionnalités du Service de langage ancien](legacy-language-service-features1.md)
