---
title: "Le reformatage du Code dans un Service de langage hérité | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- reformatting code, supporting in language services [managed package framework]
- language services [managed package framework], reformatting code
ms.assetid: 08bb3375-8fef-4f4e-9efa-0d7333bab0eb
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a2ff6152d5c9b5108dff00d9b17cb4fb2471ac4b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="reformatting-code-in-a-legacy-language-service"></a>Le reformatage du Code dans un Service de langage hérité

Dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] code source peut être remis en forme par la normalisation de l’utilisation de retraits et d’espace blanc. Cela peut inclure d’insertion ou suppression des espaces ou des tabulations au début de chaque ligne, ajoutez de nouvelles lignes entre les lignes ou en remplaçant les espaces avec onglets ou les tabulations par des espaces.  
  
>**Remarque :** insertion ou la suppression des caractères de saut de ligne peut affecter les marqueurs de points d’arrêt et les signets, mais ajout ou suppression des espaces ou des onglets n’affecte pas les marqueurs.  
  
Les utilisateurs peuvent démarrer une opération de reformatage en sélectionnant **la sélection du Format** ou **Document au Format** à partir de la **avancé** menu sur le **modifier**menu. Une opération de reformatage peut aussi être déclenchée lors de l’insertion d’un extrait de code ou un caractère particulier. Par exemple, lorsque vous tapez une accolade fermante dans c#, tout le contenu entre l’accolade ouvrante correspondante et l’accolade fermante est automatiquement mis en retrait correctement.
  
Lorsque [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] envoie le **la sélection du Format** ou **Document au Format** commande au service de langage, le <xref:Microsoft.VisualStudio.Package.ViewFilter> classe appelle la <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> méthode dans la <xref:Microsoft.VisualStudio.Package.Source> classe. Pour prendre en charge de la mise en forme que vous devez substituer la <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> méthode et fournir votre propre mise en forme du code.  
  
## <a name="enabling-support-for-reformatting"></a>L’activation de la prise en charge pour le reformatage  

Pour prendre en charge la mise en forme, les `EnableFormatSelection` paramètre de la <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> doit avoir la valeur `true` lorsque vous enregistrez votre VSPackage. Cela permet de définir la <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableFormatSelection%2A> propriété `true`. Le <xref:Microsoft.VisualStudio.Package.ViewFilter.CanReformat%2A> méthode retourne la valeur de cette propriété. Si elle retourne la valeur est true, le <xref:Microsoft.VisualStudio.Package.ViewFilter> classe appelle la <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>.  
  
## <a name="implementing-reformatting"></a>Mise en œuvre de la remise en forme

Pour implémenter le reformatage, vous devez dériver une classe à partir de la <xref:Microsoft.VisualStudio.Package.Source> classe et substituer la <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> (méthode). Le <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> objet décrit l’étendue à mettre en forme et la <xref:Microsoft.VisualStudio.Package.EditArray> objet contient les modifications apportées sur l’étendue. Notez que cette étendue peut être l’intégralité du document. Toutefois, comme il existe probablement plusieurs modifications sont apportées à l’étendue, toutes les modifications doivent être réversibles dans une seule action. Pour ce faire, encapsulez toutes les modifications dans un <xref:Microsoft.VisualStudio.Package.CompoundAction> (voir la section de « À l’aide de la classe CompoundAction » dans cette rubrique) de l’objet.

### <a name="example"></a>Exemple  

L’exemple suivant vérifie la présence d’un espace unique après chaque virgule dans la sélection, à moins que la virgule est suivie par une tabulation ou à la fin de la ligne. Les espaces de fin après la suppression de la dernière virgule dans une ligne. Consultez la section « Utilisation de la classe CompoundAction » dans cette rubrique pour savoir comment cette méthode est appelée à partir de la <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> (méthode).  

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
 
Tous les la remise en forme effectuée sur une section de code doit être réversible dans une seule action. Cela peut être accompli à l’aide un <xref:Microsoft.VisualStudio.Package.CompoundAction> classe. Cette classe encapsule un ensemble d’opérations de modification de la mémoire tampon de texte dans une opération de modification unique.  
  
### <a name="example"></a>Exemple

Voici un exemple montrant comment utiliser la <xref:Microsoft.VisualStudio.Package.CompoundAction> classe. Consultez l’exemple dans la section « Implémentation de prise en charge pour la mise en forme » dans cette rubrique pour obtenir un exemple de la `DoFormatting` (méthode).  
  
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

[Fonctionnalités de Service de langage hérité](legacy-language-service-features1.md)