---
title: Mode plan dans un service de langage hérité | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- outlining
- language services [managed package framework], outlining
- outlining, supporting in language services [managed package framework]
ms.assetid: 7b5578b4-a20a-4b94-ad4c-98687ac133b9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a6b2ba55a2e77a1f7261812a181ad780c2ef2b71
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726178"
---
# <a name="outlining-in-a-legacy-language-service"></a>Mode Plan dans un service de langage hérité
Le mode plan permet de réduire un programme complexe en vue d’une vue d’ensemble ou d’une structure. Par exemple, dans C# toutes les méthodes, peut être réduit sur une seule ligne, en n’présentant que la signature de la méthode. En outre, les structures et les classes peuvent être réduites pour afficher uniquement les noms des structures et des classes. Au sein d’une même méthode, une logique complexe peut être réduite pour afficher le déroulement global en affichant uniquement la première ligne d’instructions, comme `foreach`, `if`et `while`.

 Les services de langage hérités sont implémentés dans le cadre d’un VSPackage, mais la meilleure façon d’implémenter les fonctionnalités du service de langage consiste à utiliser les extensions MEF. Pour en savoir plus, consultez [procédure pas à pas : mode plan](../../extensibility/walkthrough-outlining.md).

> [!NOTE]
> Nous vous recommandons de commencer à utiliser la nouvelle API Editor dès que possible. Cela améliore les performances de votre service de langage et vous permet de tirer parti des nouvelles fonctionnalités de l’éditeur.

## <a name="enabling-support-for-outlining"></a>Activation de la prise en charge du mode plan
 L’entrée de Registre `AutoOutlining` a la valeur 1 pour activer le mode plan automatique. Le mode plan automatique définit une analyse de la source entière lorsqu’un fichier est chargé ou modifié pour identifier les zones masquées et afficher les glyphes en mode plan. Le mode plan peut également être contrôlé manuellement par l’utilisateur.

 La valeur de l’entrée de Registre `AutoOutlining` peut être obtenue via la propriété <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> de la classe <xref:Microsoft.VisualStudio.Package.LanguagePreferences>. L’entrée de Registre `AutoOutlining` peut être initialisée avec un paramètre nommé de l’attribut <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> (pour plus d’informations, consultez [inscription d’un service de langage hérité](../../extensibility/internals/registering-a-legacy-language-service1.md) ).

## <a name="the-hidden-region"></a>Zone masquée
 Pour fournir un mode plan, votre service de langage doit prendre en charge les zones masquées. Il s’agit de plusieurs étendues de texte qui peuvent être développées ou réduites. Les zones masquées peuvent être délimitées par des symboles de langage standard, tels que des accolades, ou par des symboles personnalisés. Par exemple, C# a une paire`#region`/`#endregion`qui délimite une zone masquée.

 Les zones masquées sont gérées par un gestionnaire de zones masquées, qui est exposé en tant qu’interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>.

 Le mode plan utilise les zones masquées dans l’interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegion> et contient l’étendue de la zone masquée, l’état visible actuel et la bannière à afficher lorsque l’étendue est réduite.

 L’analyseur de service de langage utilise la méthode <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> pour ajouter une nouvelle zone masquée avec le comportement par défaut pour les zones masquées, tandis que la méthode <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> vous permet de personnaliser l’apparence et le comportement du plan. Une fois les zones masquées attribuées à la session de la zone masquée, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gère les zones masquées pour le service de langage.

 Si vous devez déterminer à quel moment la session de la zone masquée est détruite, une zone masquée est modifiée ou vous devez vous assurer qu’une zone masquée spécifique est visible. vous devez dériver une classe de la classe <xref:Microsoft.VisualStudio.Package.Source> et remplacer les méthodes appropriées, <xref:Microsoft.VisualStudio.Package.Source.OnBeforeSessionEnd%2A>, <xref:Microsoft.VisualStudio.Package.Source.OnHiddenRegionChange%2A>et <xref:Microsoft.VisualStudio.Package.Source.MakeBaseSpanVisible%2A>, respectivement.

### <a name="example"></a>Exemple
 Voici un exemple simplifié de création de zones masquées pour toutes les paires d’accolades. Il est supposé que le langage fournit une mise en correspondance des accolades et que les accolades à mettre en correspondance incluent au moins les accolades ({et}). Cette approche est fournie à titre d’illustration uniquement. Une implémentation complète aurait une gestion complète des cas dans <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>. Cet exemple montre également comment définir la préférence de <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> sur `true` temporairement. Une alternative consiste à spécifier le paramètre `AutoOutlining` nommé dans l’attribut `ProvideLanguageServiceAttribute` de votre package de langage.

 Cet exemple suppose des C# règles pour les commentaires, les chaînes et les littéraux.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace MyLanguagePackage
{

    public class MyLanguageService : LanguageService
    {
        private LanguagePreferences m_preferences;

        public override LanguagePreferences  GetLanguagePreferences()
        {
            if (m_preferences == null)
            {
                m_preferences = new LanguagePreferences(this.Site,
                                                        typeof(MyLanguageService).GUID,
                                                        Name);
                m_preferences.Init();
                // Temporarily enabled auto-outlining
                m_preferences.AutoOutlining = true;
            }
            return m_preferences;
        }

        public override AuthoringScope  ParseSource(ParseRequest req)
        {
            Source source = (Source) this.GetSource(req.FileName);
            switch (req.Reason)
            {
               case ParseReason.HighlightBraces:
               case ParseReason.MatchBraces:
               case ParseReason.MemberSelectAndHighlightBraces:
                  if (source.Braces != null)
                  {
                      foreach (TextSpan[] brace in source.Braces)
                      {
                         if (brace.Length == 2)
                         {
                             if (req.Sink.HiddenRegions == true
                                   && source.GetText(brace[0]).Equals("{")
                                   && source.GetText(brace[1]).Equals("}"))
                             {
                                //construct a TextSpan of everything between the braces
                                TextSpan hideSpan = new TextSpan();
                                hideSpan.iStartIndex = brace[0].iStartIndex;
                                hideSpan.iStartLine = brace[0].iStartLine;
                                hideSpan.iEndIndex = brace[1].iEndIndex;
                                hideSpan.iEndLine = brace[1].iEndLine;
                                req.Sink.ProcessHiddenRegions = true;
                                req.Sink.AddHiddenRegion(hideSpan);
                             }
                             req.Sink.MatchPair(brace[0], brace[1], 1);
                         }
                         else if (brace.Length >= 3)
                             req.Sink.MatchTriple(brace[0], brace[1], brace[2], 1);
                  }
        }
                   break;
               default:
                   break;
      }
            // Must always return a valid AuthoringScope object.
            return new MyAuthoringScope();
        }
    }
}
```

## <a name="see-also"></a>Voir aussi
- [Fonctionnalités du service de langage hérité](../../extensibility/internals/legacy-language-service-features1.md)
- [Inscription d’un service de langage hérité](../../extensibility/internals/registering-a-legacy-language-service1.md)