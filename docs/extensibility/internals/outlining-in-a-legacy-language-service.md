---
title: "Mode plan dans un Service de langage h&#233;rit&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "mode Plan"
  - "services de langage (framework package managé), le mode plan"
  - "mode plan, prise en charge dans les services de langage (framework package managé)"
ms.assetid: 7b5578b4-a20a-4b94-ad4c-98687ac133b9
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Mode plan dans un Service de langage h&#233;rit&#233;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Le mode plan permet de réduire un programme complexe dans une vue d’ensemble ou un plan. Par exemple, en c\#, toutes les méthodes peuvent être réduites à une seule ligne, n'indiquant que la signature de méthode. En outre, des structures et des classes peuvent être réduits pour afficher uniquement les noms des classes et structures. À l’intérieur d’une méthode unique, une logique complexe peut être réduite pour montrer le flux global en affichant uniquement la première ligne des instructions telles que `foreach`, `if`, et `while`.  
  
 Les services de langage ancien sont implémentés en tant que partie d’un VSPackage, mais la plus récente pour implémenter les fonctionnalités du service de langage consiste à utiliser les extensions MEF. Pour en savoir plus, consultez [Procédure pas à pas : mise en relief](../../extensibility/walkthrough-outlining.md).  
  
> [!NOTE]
>  Nous vous recommandons de commencer à utiliser l’API de l’éditeur de nouveau dès que possible. Cela améliorer les performances de votre service de langage et vous permettent de tirer parti des nouvelles fonctionnalités de l’éditeur.  
  
## L’activation de la prise en charge pour le mode plan  
 Le `AutoOutlining` est définie sur 1 pour activer le mode plan automatique. Mode plan automatique configure une analyse de la source complète lorsqu’un fichier est chargé ou modifié afin d’identifier les zones masquées et afficher les glyphes en mode plan. Mode plan peut également être contrôlé manuellement par l’utilisateur.  
  
 La valeur de la `AutoOutlining` entrée de Registre peut être obtenue via la <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> propriété sur la <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe. La `AutoOutlining` entrée de Registre peut être initialisée avec un paramètre nommé pour la <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> attribut \(voir [L’inscription d’un Service de langage](../../extensibility/internals/registering-a-legacy-language-service1.md) Pour plus d’informations\).  
  
## La zone masquée  
 Pour fournir la mise en relief, votre service de langage doit prendre en charge les zones masquées. Il s’agit d’étendues de texte qui peut être développée ou réduite. Les zones masquées peuvent être délimitées par des symboles de langage standard, tels que des accolades, ou par des symboles personnalisés. Par exemple, c\# a une `#region`\/`#endregion` paire qui délimite une zone masquée.  
  
 Les zones masquées sont gérées par un gestionnaire de zone masquée, qui est exposé comme le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> interface.  
  
 Mode plan utilise les zones masquées du <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegion> d’interface et contient l’étendue de la zone masquée, l’état de visibilité actuel et la bannière à afficher lorsque l’intervalle est réduit.  
  
 L’Analyseur de service de langage utilise le <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> pour ajouter une nouvelle région masquée avec le comportement par défaut pour les zones masquées, tandis que le <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> permet de personnaliser l’apparence et le comportement de la structure du. Une fois que les zones masquées sont fournies à la session de la zone masquée, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gère les zones masquées pour le service de langage.  
  
 Si vous avez besoin déterminer quand la session de la zone masquée est détruite, une zone masquée est modifiée, ou vous devez vous assurer de qu'une région particulière masquée est visible ; Vous devez dériver une classe à partir de la <xref:Microsoft.VisualStudio.Package.Source> classe et substituer les méthodes appropriées, <xref:Microsoft.VisualStudio.Package.Source.OnBeforeSessionEnd%2A>, <xref:Microsoft.VisualStudio.Package.Source.OnHiddenRegionChange%2A>, et <xref:Microsoft.VisualStudio.Package.Source.MakeBaseSpanVisible%2A>, respectivement.  
  
### Exemple  
 Voici un exemple simplifié de la création des zones masquées pour toutes les paires d’accolades. Il est supposé que le langage fournit accolades correspondantes, ainsi que les accolades à mettre en correspondance inclure au moins les accolades \({et}\). Cette approche est qu’à titre indicatif. Une implémentation complète aurait une gestion complète des cas de <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>. Cet exemple montre également comment définir le <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> préférence `true` temporairement. Une alternative consiste à spécifier la `AutoOutlining` nommé dans le `ProvideLanguageServiceAttribute` attribut dans votre package de langue.  
  
 Cet exemple part du principe que les règles c\# pour les commentaires, les chaînes et littéraux.  
  
```c#  
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
  
## Voir aussi  
 [Fonctionnalités du Service de langage ancien](../../extensibility/internals/legacy-language-service-features1.md)   
 [L’inscription d’un Service de langage](../../extensibility/internals/registering-a-legacy-language-service1.md)