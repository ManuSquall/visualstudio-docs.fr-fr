---
title: "Prise en charge de la barre de Navigation dans un Service de langage hérité | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Navigation bar, supporting in language services [managed package framework]
- language services [managed package framework], Navigation bar
ms.assetid: 2d301ee6-4523-4b82-aedb-be43f352978e
caps.latest.revision: 16
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 88636468da333fd9200f8661d88af6e7fdeedc59
ms.lasthandoff: 02/22/2017

---
# <a name="support-for-the-navigation-bar-in-a-legacy-language-service"></a>Prise en charge de la barre de Navigation dans un Service de langage hérité
La barre de Navigation en haut de l’affichage de l’éditeur affiche les types et membres dans le fichier. Types sont affichés dans la liste déroulante gauche, et les membres sont affichés dans le droit de la liste déroulante. Lorsque l’utilisateur sélectionne un type, le point d’insertion est placé sur la première ligne du type. Lorsque l’utilisateur sélectionne un membre, le point d’insertion est placé sur la définition du membre. Les zones de liste déroulante sont mis à jour pour refléter l’emplacement actuel du signe insertion.  
  
## <a name="displaying-and-updating-the-navigation-bar"></a>Affichage et mise à jour de la barre de Navigation  
 Pour prendre en charge de la barre de Navigation, vous devez dériver une classe à partir de la <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>classe et implémenter la <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>méthode.</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> </xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> Lorsque votre service de langage est donnée à une fenêtre de code, la base de <xref:Microsoft.VisualStudio.Package.LanguageService>classe instancie le <xref:Microsoft.VisualStudio.Package.CodeWindowManager>, qui contient le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>objet représentant la fenêtre de code.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> </xref:Microsoft.VisualStudio.Package.CodeWindowManager> </xref:Microsoft.VisualStudio.Package.LanguageService> Le <xref:Microsoft.VisualStudio.Package.CodeWindowManager>objet reçoit ensuite un nouveau <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>objet.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> </xref:Microsoft.VisualStudio.Package.CodeWindowManager> Le <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>méthode obtient un <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>objet.</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> </xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> Si vous retournez une instance de votre <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>(classe), le <xref:Microsoft.VisualStudio.Package.CodeWindowManager>appelle votre <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>pour remplir l’intérieur répertorie et le transmet votre <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>objet la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] déroulante barre manager.</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> </xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> </xref:Microsoft.VisualStudio.Package.CodeWindowManager> </xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> La liste déroulante barre manager, à son tour, appelle la <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.SetDropdownBar%2A>méthode sur votre <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>objet pour établir le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar>objet qui contient les deux barres de menu déroulant.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar> </xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> </xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.SetDropdownBar%2A>  
  
 Lorsque le point d’insertion se déplace, les <xref:Microsoft.VisualStudio.Package.LanguageService.OnIdle%2A>des appels de méthode du <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A>méthode.</xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> </xref:Microsoft.VisualStudio.Package.LanguageService.OnIdle%2A> base <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A>de méthode appelle la <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>méthode dans votre <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>classe pour mettre à jour l’état de la barre de Navigation.</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> </xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> </xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> Passer d’un ensemble de <xref:Microsoft.VisualStudio.Package.DropDownMember>objets à cette méthode.</xref:Microsoft.VisualStudio.Package.DropDownMember> Chaque objet représente une entrée dans la liste déroulante.  
  
## <a name="the-contents-of-the-navigation-bar"></a>Le contenu de la barre de Navigation  
 La barre de Navigation contient généralement une liste de types et une liste de membres. La liste des types inclut tous les types disponibles dans le fichier source actuel. Les noms de type incluent les informations d’espace de noms complet. Voici un exemple de code c# avec deux types :  
  
```c#  
namespace TestLanguagePackage  
{  
    public class TestLanguageService  
    {  
        internal struct Token  
        {  
            int tokenID;  
        }  
        private Tokens[] tokens;  
        private string serviceName;  
    }  
}  
```  
  
 Affiche la liste des types `TestLanguagePackage.TestLanguageService` et `TestLanguagePackage.TestLanguageService.Tokens`.  
  
 La liste des membres affiche les membres du type sélectionné dans la liste des types disponibles. À l’aide de l’exemple de code ci-dessus, si `TestLanguagePackage.TestLanguageService` est le type qui est sélectionné, la liste des membres contient les membres privés `tokens` et `serviceName`. La structure interne `Token` n’est pas affichée.  
  
 Vous pouvez implémenter la liste des membres pour afficher le nom d’un membre en gras lorsque le point d’insertion est placé à l’intérieur. Membres peuvent également être affichés dans grisés texte, indiquant qu’ils ne sont pas dans la portée dans laquelle le point d’insertion est positionné.  
  
## <a name="enabling-support-for-the-navigation-bar"></a>Prise en charge de la barre de Navigation  
 Pour activer la prise en charge de la barre de Navigation, vous devez définir le `ShowDropdownBarOption` paramètre de la <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>l’attribut `true`.</xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> Ce paramètre définit la <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A>propriété.</xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> Pour prendre en charge de la barre de Navigation, vous devez implémenter l' <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>objet dans la <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>méthode sur la <xref:Microsoft.VisualStudio.Package.LanguageService>classe.</xref:Microsoft.VisualStudio.Package.LanguageService> </xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> </xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>  
  
 Dans votre implémentation de la <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>(méthode), si la <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A>est définie sur `true`, vous pouvez retourner un <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>objet.</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> </xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> </xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> Si vous ne renvoyez pas l’objet, la barre de Navigation n’est pas affichée.  
  
 L’option pour afficher la barre de Navigation peut être définie par l’utilisateur, il est donc possible pour ce contrôle doivent être réinitialisées lorsque l’affichage de l’éditeur est ouverte. L’utilisateur doit fermer et rouvrir la fenêtre de l’éditeur avant du modifier.  
  
## <a name="implementing-support-for-the-navigation-bar"></a>L’implémentation de prise en charge de la barre de Navigation  
 Le <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>méthode prend deux listes (une pour chaque liste déroulante) et deux valeurs représentant la sélection actuelle dans chaque liste.</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> Les listes et les valeurs de sélection peuvent être mis à jour, auquel cas la <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>méthode doit retourner `true` pour indiquer que les listes ont changé.</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>  
  
 Comme la sélection change dans les types de liste déroulante, la liste des membres doive être mis à jour pour refléter le nouveau type. Ce qui est affiché dans la liste des membres peut être :  
  
-   La liste des membres pour le type actuel.  
  
-   Tous les membres disponibles dans la source de fichier, mais avec tous les membres pas dans le type actuel affichent dans le texte grisé. L’utilisateur peut toujours sélectionner les membres grisée, ils peuvent être utilisés pour la navigation rapide, mais la couleur indique qu’ils ne sont pas partie du type actuellement sélectionné.  
  
 Une implémentation de la <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>méthode effectue généralement les étapes suivantes :</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>  
  
1.  Obtenir une liste de déclarations actuelles pour le fichier source.  
  
     Il existe plusieurs manières de remplir les listes. Une approche consiste à créer une méthode personnalisée de votre version de la <xref:Microsoft.VisualStudio.Package.LanguageService>classe qui appelle le <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>méthode avec la raison analyse personnalisée qui retourne une liste de toutes les déclarations.</xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> </xref:Microsoft.VisualStudio.Package.LanguageService> Une autre approche peut consister à appeler le <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>méthode directement à partir de la <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>méthode avec la raison pour laquelle l’analyse personnalisée.</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> </xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Une troisième approche peut consister à mettre en cache les déclarations dans la <xref:Microsoft.VisualStudio.Package.AuthoringScope>classe retournée par la dernière opération d’analyse complète de la <xref:Microsoft.VisualStudio.Package.LanguageService>classe et de le récupérer à partir de la <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>(méthode).</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> </xref:Microsoft.VisualStudio.Package.LanguageService> </xref:Microsoft.VisualStudio.Package.AuthoringScope>  
  
2.  Remplir ou mettre à jour la liste des types.  
  
     Le contenu de la liste des types peut mettre à jour lorsque la source a changé ou si vous avez choisi de modifier le style du texte des types en fonction de la position actuelle du signe insertion. Notez que cette position est passée à la <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>méthode.</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>  
  
3.  Déterminer le type pour le sélectionner dans la liste des types en fonction de la position actuelle du signe insertion.  
  
     Vous pouvez rechercher les déclarations qui ont été obtenues à l’étape 1 pour rechercher le type qui définit la position actuelle du point d’insertion et puis rechercher la liste de types de ce type déterminer son index dans la liste des types.  
  
4.  Remplir ou mettre à jour la liste des membres en fonction du type sélectionné.  
  
     La liste des membres reflète ce qui est actuellement affiché dans le **membres** liste déroulante. Le contenu de la liste des membres peut doivent être mis à jour si la source a changé ou si vous affichez uniquement les membres du type sélectionné et le type sélectionné a changé. Si vous choisissez d’afficher tous les membres dans le fichier source, le style du texte de chaque membre dans la liste doit être mis à jour si le type sélectionné a été modifié.  
  
5.  Déterminer le membre à sélectionner dans la liste des membres en fonction de la position actuelle du signe insertion.  
  
     Rechercher les déclarations qui ont été obtenues à l’étape 1 pour le membre qui contient la position actuelle du point d’insertion, puis recherchez la liste des membres de ce membre déterminer son index dans la liste des membres.  
  
6.  Retourner `true` si des modifications ont été apportées pour les listes ou les sélections dans les listes.
