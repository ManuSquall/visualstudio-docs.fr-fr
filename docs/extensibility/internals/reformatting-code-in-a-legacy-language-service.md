---
title: Reformatage du code dans un service de langage hérité | Microsoft Docs
description: En savoir plus sur l’activation de la prise en charge du reformatage du code source pour un service de langage hérité Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- reformatting code, supporting in language services [managed package framework]
- language services [managed package framework], reformatting code
ms.assetid: 08bb3375-8fef-4f4e-9efa-0d7333bab0eb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0198ef145c3fbf6d0edcc6a95954794597fce0b2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99875586"
---
# <a name="reformatting-code-in-a-legacy-language-service"></a>Reformatage du code dans un service de langage hérité

Dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] le code source peut être reformaté en normalisant l’utilisation des retraits et des espaces. Cela peut inclure l’insertion ou la suppression d’espaces ou de tabulations au début de chaque ligne, l’ajout de nouvelles lignes entre les lignes ou le remplacement des espaces par des tabulations ou des tabulations par des espaces.

> [!NOTE]
> L’insertion ou la suppression de caractères de saut de ligne peut affecter des marqueurs comme des points d’arrêt et des signets, mais l’ajout ou la suppression d’espaces ou de tabulations n’affecte pas les marqueurs

Les utilisateurs peuvent démarrer une opération de reformatage en sélectionnant **formater la sélection** ou **mettre le document en forme** dans le menu **avancé** du menu **Edition** . Une opération de reformatage peut également être déclenchée quand un extrait de code ou un caractère particulier est inséré. Par exemple, lorsque vous tapez une accolade fermante en C#, tout ce qui se trouve entre l’accolade ouvrante correspondante et l’accolade fermante est automatiquement mis en retrait au niveau approprié.

Lorsque [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] envoie la commande **mettre en forme la sélection** ou mettre le document en **forme** au service de langage, la <xref:Microsoft.VisualStudio.Package.ViewFilter> classe appelle la <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> méthode dans la <xref:Microsoft.VisualStudio.Package.Source> classe. Pour prendre en charge la mise en forme, vous devez substituer la <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> méthode et fournir votre propre code de mise en forme.

## <a name="enabling-support-for-reformatting"></a>Activation de la prise en charge du reformatage

Pour prendre en charge la mise en forme, le `EnableFormatSelection` paramètre de <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> doit avoir la valeur `true` lorsque vous inscrivez votre VSPackage. Cela affecte la <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableFormatSelection%2A> valeur à la propriété `true` . La <xref:Microsoft.VisualStudio.Package.ViewFilter.CanReformat%2A> méthode retourne la valeur de cette propriété. Si elle retourne la valeur true, la <xref:Microsoft.VisualStudio.Package.ViewFilter> classe appelle <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> .

## <a name="implementing-reformatting"></a>Implémentation du reformatage

Pour implémenter le reformatage, vous devez dériver une classe de la <xref:Microsoft.VisualStudio.Package.Source> classe et substituer la <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> méthode. L' <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> objet décrit l’étendue à mettre en forme et l' <xref:Microsoft.VisualStudio.Package.EditArray> objet contient les modifications apportées à l’étendue. Notez que cette étendue peut être le document entier. Toutefois, étant donné qu’il y a probablement plusieurs modifications apportées à l’étendue, toutes les modifications doivent être réversibles en une seule action. Pour ce faire, encapsulez toutes les modifications dans un <xref:Microsoft.VisualStudio.Package.CompoundAction> objet (consultez la section « utilisation de la classe CompoundAction » dans cette rubrique).

### <a name="example"></a>Exemple

L’exemple suivant vérifie qu’il y a un seul espace après chaque virgule dans la sélection, sauf si la virgule est suivie d’un onglet ou se trouve à la fin de la ligne. Les espaces de fin situés après la dernière virgule d’une ligne sont supprimés. Consultez la section « utilisation de la classe CompoundAction » dans cette rubrique pour voir comment cette méthode est appelée à partir de la <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> méthode.

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

## <a name="using-the-compoundaction-class"></a>Utilisation de la classe CompoundAction

Tout le reformatage effectué sur une section de code doit être réversible en une seule action. Cela peut être accompli à l’aide d’une <xref:Microsoft.VisualStudio.Package.CompoundAction> classe. Cette classe encapsule un ensemble d’opérations de modification sur la mémoire tampon de texte en une seule opération de modification.

### <a name="example"></a>Exemple

Voici un exemple d’utilisation de la <xref:Microsoft.VisualStudio.Package.CompoundAction> classe. Consultez l’exemple de la section « implémentation de la prise en charge de la mise en forme » dans cette rubrique pour obtenir un exemple de la `DoFormatting` méthode.

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

- [Fonctionnalités du service de langage hérité](legacy-language-service-features1.md)
