---
title: Le mode plan dans un Service de langage hérité | Microsoft Docs
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
- outlining
- language services [managed package framework], outlining
- outlining, supporting in language services [managed package framework]
ms.assetid: 7b5578b4-a20a-4b94-ad4c-98687ac133b9
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 356b3d49fa8eb74ef2352e6ba36597d1c39fecf4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51751541"
---
# <a name="outlining-in-a-legacy-language-service"></a>Mode Plan dans un service de langage hérité
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Le mode plan permet de réduire un programme complexe dans une vue d’ensemble ou un plan. Par exemple, en c#, toutes les méthodes peuvent être réduits en une seule ligne, en affichant uniquement la signature de méthode. En outre, les structures et les classes peuvent être réduites pour afficher uniquement les noms des classes et structures. À l’intérieur d’une méthode unique, une logique complexe peut être réduite pour afficher le flux global en affichant uniquement la première ligne des instructions telles que `foreach`, `if`, et `while`.  
  
 Services de langage hérité sont implémentés en tant que partie d’un VSPackage, mais la plus récente pour implémenter des fonctionnalités de service de langage consiste à utiliser des extensions MEF. Pour plus d’informations, consultez [procédure pas à pas : mise en relief](../../extensibility/walkthrough-outlining.md).  
  
> [!NOTE]
>  Nous vous recommandons de commencer à utiliser le nouvel éditeur API dès que possible. Cela améliorer les performances de votre service de langage et vous permettent de tirer parti des nouvelles fonctionnalités de l’éditeur.  
  
## <a name="enabling-support-for-outlining"></a>L’activation de la prise en charge pour le mode plan  
 Le `AutoOutlining` entrée de Registre est définie sur 1 pour activer le mode plan automatique. Le mode plan automatique configure une analyse de la source entier lorsqu’un fichier est chargé ou modifié afin d’identifier les zones masquées et afficher les glyphes en mode plan. Le mode plan peut également être contrôlé manuellement par l’utilisateur.  
  
 La valeur de la `AutoOutlining` entrée de Registre peut être obtenue via la <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> propriété sur le <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe. Le `AutoOutlining` entrée de Registre peut être initialisée avec un paramètre nommé pour le <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> attribut (voir [l’inscription d’un Service de langage hérité](../../extensibility/internals/registering-a-legacy-language-service1.md) pour plus d’informations).  
  
## <a name="the-hidden-region"></a>La zone masquée  
 Pour fournir le mode plan, votre service de langage doit prendre en charge les zones masquées. Il s’agit des étendues de texte qui peut être développée ou réduite. Les zones masquées peuvent être délimités par des symboles de langage standard, tels que des accolades, ou par des symboles personnalisés. Par exemple, c# a un `#region` / `#endregion` paire qui délimite une zone masquée.  
  
 Les zones masquées sont gérés par un gestionnaire de zone masquée, qui est exposé en tant que le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> interface.  
  
 Le mode plan utilise les zones masquées le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegion> interface et contient l’étendue de la zone masquée, l’état visible actuel et la bannière à afficher lorsque l’étendue est réduite.  
  
 L’Analyseur de service de langage utilise le <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> méthode pour ajouter une nouvelle zone masquée avec le comportement par défaut pour les zones masquées, tandis que le <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> méthode vous permet de personnaliser l’apparence et le comportement du contour. Une fois que les zones masquées sont fournis pour la session de la zone masquée, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] gère les zones masquées pour le service de langage.  
  
 Si vous avez besoin déterminer quand la session de zone masquée est détruite, une zone masquée est modifiée, ou vous devez vous assurer de qu'une zone masquée particulière est visible ; Vous devez dériver une classe à partir de la <xref:Microsoft.VisualStudio.Package.Source> classe et substituer les méthodes appropriées, <xref:Microsoft.VisualStudio.Package.Source.OnBeforeSessionEnd%2A>, <xref:Microsoft.VisualStudio.Package.Source.OnHiddenRegionChange%2A>, et <xref:Microsoft.VisualStudio.Package.Source.MakeBaseSpanVisible%2A>, respectivement.  
  
### <a name="example"></a>Exemple  
 Voici un exemple simplifié de la création de zones masquées pour toutes les paires d’accolades. Il est supposé que le langage fournit la correspondance des accolades, ainsi que les accolades à mettre en correspondance inclure au moins les accolades ({et}). Cette approche est uniquement à des fins d’illustration. Une implémentation complète aurait une gestion complète des cas dans <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>. Cet exemple montre également comment définir le <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> préférence aux `true` temporairement. Une alternative consiste à spécifier le `AutoOutlining` nommé de paramètre dans le `ProvideLanguageServiceAttribute` attribut dans votre package de langage.  
  
 Cet exemple part du principe que les règles c# pour les commentaires, chaînes et littéraux.  
  
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
 [Fonctionnalités de Service de langage hérité](../../extensibility/internals/legacy-language-service-features1.md)   
 [Inscription d’un service de langage hérité](../../extensibility/internals/registering-a-legacy-language-service1.md)

