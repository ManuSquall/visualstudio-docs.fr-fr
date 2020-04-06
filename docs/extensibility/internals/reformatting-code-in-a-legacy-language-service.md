---
title: Reformatting Code in a Legacy Language Service (en anglais seulement) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- reformatting code, supporting in language services [managed package framework]
- language services [managed package framework], reformatting code
ms.assetid: 08bb3375-8fef-4f4e-9efa-0d7333bab0eb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dd3e83c7299298b16a6fb3178b189479a80e1728
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705911"
---
# <a name="reformatting-code-in-a-legacy-language-service"></a>Reformatage du code dans un service de langage hérité

Dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] le code source peut être reformaté en normalisant l’utilisation des indentations et de l’espace blanc. Il peut s’agir d’insérer ou de retirer des espaces ou des onglets au début de chaque ligne, d’ajouter de nouvelles lignes entre les lignes ou de remplacer les espaces par des onglets ou des onglets par des espaces.

> [!NOTE]
> L’insertion ou la suppression de caractères newline peuvent affecter des marqueurs tels que des points de rupture et des signets, mais l’ajout ou la suppression d’espaces ou d’onglets n’affecte pas les marqueurs.

Les utilisateurs peuvent commencer une opération de reformatage en sélectionnant **format Selection** ou **Format Document** à partir du menu **Avancé** sur le menu **Edit.** Une opération de reformatation peut également être déclenchée lorsqu’un extrait de code ou un caractère particulier est inséré. Par exemple, lorsque vous tapez une accolade de fermeture dans le C, tout ce qui se situe entre l’attelle ouverte assortie et l’attelle rapprochée est automatiquement en retrait au niveau approprié.

Lorsque [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vous envoiez la commande **Format Selection** ou Format **Document** au service linguistique, <xref:Microsoft.VisualStudio.Package.ViewFilter> la classe appelle la <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> méthode dans la <xref:Microsoft.VisualStudio.Package.Source> classe. Pour prendre en charge le <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> formatage, vous devez passer outre à la méthode et fournir votre propre code de formatage.

## <a name="enabling-support-for-reformatting"></a>Permettre le soutien à la reformatage

Pour prendre en `EnableFormatSelection` charge le <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> formatage, `true` le paramètre de la doit être défini à l’enregistrement de votre VSPackage. Cela définit <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableFormatSelection%2A> la `true`propriété à . La <xref:Microsoft.VisualStudio.Package.ViewFilter.CanReformat%2A> méthode retourne la valeur de cette propriété. Si elle revient <xref:Microsoft.VisualStudio.Package.ViewFilter> vrai, <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>la classe appelle le .

## <a name="implementing-reformatting"></a>Mise en œuvre de la reformatation

Pour mettre en œuvre reformatage, vous devez tirer une classe de la <xref:Microsoft.VisualStudio.Package.Source> classe et passer outre à la <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> méthode. L’objet <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> décrit la portée <xref:Microsoft.VisualStudio.Package.EditArray> au format et l’objet contient les modifications effectuées sur la travée. Notez que cette portée peut être l’ensemble du document. Cependant, comme il est probable qu’il y ait plusieurs modifications apportées à la travée, toutes les modifications devraient être réversibles en une seule action. Pour ce faire, enveloppez <xref:Microsoft.VisualStudio.Package.CompoundAction> tous les changements dans un objet (voir la section « Utiliser la classe CompoundAction » dans ce sujet).

### <a name="example"></a>Exemple

L’exemple suivant garantit qu’il y a un espace unique après chaque virgule dans la sélection, à moins que la virgule ne soit suivie d’un onglet ou qu’elle se trouve à la fin de la ligne. Les espaces de fuite après la dernière virgule d’une ligne sont supprimés. Voir la section « Utiliser la classe CompoundAction » dans ce <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> sujet pour voir comment cette méthode est appelée à partir de la méthode.

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

Toutes les reformatations effectuées sur une section de code doivent être réversibles en une seule action. Cela peut être <xref:Microsoft.VisualStudio.Package.CompoundAction> accompli à l’aide d’une classe. Cette classe enveloppe un ensemble d’opérations de modification sur le tampon de texte en une seule opération de modification.

### <a name="example"></a>Exemple

Voici un exemple de la <xref:Microsoft.VisualStudio.Package.CompoundAction> façon d’utiliser la classe. Voir l’exemple dans la section « Soutien à la mise `DoFormatting` en œuvre pour le formatage » dans ce sujet, par exemple de la méthode.

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
