---
title: Décrivant dans un service de langue héritée (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- outlining
- language services [managed package framework], outlining
- outlining, supporting in language services [managed package framework]
ms.assetid: 7b5578b4-a20a-4b94-ad4c-98687ac133b9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: be485a0e7406d49c4dcce77958c720e0b62504b6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706812"
---
# <a name="outlining-in-a-legacy-language-service"></a>Mode Plan dans un service de langage hérité
L’exposé permet d’effondrer un programme complexe en vue d’être aperçu ou en contour. Par exemple, dans C, toutes les méthodes peuvent être effondrées en une seule ligne, ne montrant que la signature de la méthode. En outre, les structures et les classes peuvent être effondrées pour montrer seulement les noms des structures et des classes. À l’intérieur d’une seule méthode, la logique complexe peut être `foreach`effondrée `if`pour `while`montrer le flux global en montrant seulement la première ligne de déclarations telles que , , et .

 Les services linguistiques hérités sont mis en œuvre dans le cadre d’un VSPackage, mais la nouvelle façon de mettre en œuvre des fonctionnalités de service linguistique est d’utiliser des extensions MEF. Pour en savoir plus, voir [Procédure pas à pas: Outlineing](../../extensibility/walkthrough-outlining.md).

> [!NOTE]
> Nous vous recommandons de commencer à utiliser le nouvel éditeur API dès que possible. Cela améliorera les performances de votre service linguistique et vous permettra de profiter des nouvelles fonctionnalités de l’éditeur.

## <a name="enabling-support-for-outlining"></a>Permettre le soutien à l’énoncé
 L’inscription `AutoOutlining` au registre est réglée à 1 pour permettre l’inscription automatique. La mise en scène automatique met en place un analyse de toute la source lorsqu’un fichier est chargé ou modifié afin d’identifier les régions cachées et de montrer les glyphes décrivants. La mise en ligne peut également être contrôlée manuellement par l’utilisateur.

 La valeur `AutoOutlining` de l’entrée du <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> registre peut <xref:Microsoft.VisualStudio.Package.LanguagePreferences> être obtenue par l’intermédiaire de la propriété sur la classe. L’inscription `AutoOutlining` au registre peut être parasétisée avec un paramètre désigné à l’attribut <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> (voir [l’enregistrement d’un service de langue héritée](../../extensibility/internals/registering-a-legacy-language-service1.md) pour plus de détails).

## <a name="the-hidden-region"></a>La région cachée
 Pour fournir une mise en service, votre service linguistique doit soutenir les régions cachées. Ce sont des travées de texte qui peuvent être élargies ou effondrées. Les régions cachées peuvent être délimitées par des symboles linguistiques standard, tels que des accolades bouclées ou par des symboles personnalisés. Par exemple, Cmd `#region` / `#endregion` a une paire qui délimite une région cachée.

 Les régions cachées sont gérées par <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> un gestionnaire de région caché, qui est exposé comme l’interface.

 Décrivant utilise des régions cachées l’interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegion> et contiennent la portée de la région cachée, l’état visible actuel, et la bannière à montrer lorsque la travée est effondrée.

 Le parser de <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> service linguistique utilise la méthode pour ajouter une nouvelle <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> région cachée avec le comportement par défaut pour les régions cachées, tandis que la méthode vous permet de personnaliser l’apparence et le comportement du contour. Une fois que les régions [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] cachées sont données à la session de la région cachée, gère les régions cachées pour le service linguistique.

 Si vous devez déterminer quand la session de la région cachée est détruite, une région cachée est changée, ou vous devez vous assurer qu’une région cachée particulière est visible; vous devez tirer une <xref:Microsoft.VisualStudio.Package.Source> classe de la classe <xref:Microsoft.VisualStudio.Package.Source.OnBeforeSessionEnd%2A> <xref:Microsoft.VisualStudio.Package.Source.OnHiddenRegionChange%2A>et <xref:Microsoft.VisualStudio.Package.Source.MakeBaseSpanVisible%2A>passer outre les méthodes appropriées, , , et , respectivement.

### <a name="example"></a>Exemple
 Voici un exemple simplifié de création de régions cachées pour toutes les paires d’accolades bouclées. On suppose que la langue fournit l’appariement d’accolade, et que les accolades à assortir incluent au moins les accolades bouclées (et ' ). Cette approche n’est qu’à des fins d’illustration. Une mise en œuvre complète <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>aurait un traitement complet des cas dans . Cet exemple montre également <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> comment `true` définir la préférence à temporairement. Une alternative consiste `AutoOutlining` à spécifier le paramètre désigné dans l’attribut `ProvideLanguageServiceAttribute` de votre paquet linguistique.

 Cet exemple suppose les règles de C pour les commentaires, les chaînes et les littérals.

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
