---
title: Soutien à la barre de navigation dans un service de langue héritée (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Navigation bar, supporting in language services [managed package framework]
- language services [managed package framework], Navigation bar
ms.assetid: 2d301ee6-4523-4b82-aedb-be43f352978e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f86dabb0594b1e33c45808efb387fcbe313e3de3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704865"
---
# <a name="support-for-the-navigation-bar-in-a-legacy-language-service"></a>Prise en charge de la barre de navigation dans un service de langage hérité
La barre de navigation en haut de la vue de l’éditeur affiche les types et les membres du fichier. Les types sont indiqués dans le décrochage gauche, et les membres sont indiqués dans le décrochage droit. Lorsque l’utilisateur sélectionne un type, le caret est placé sur la première ligne du type. Lorsque l’utilisateur choisit un membre, le caret est placé sur la définition du membre. Les boîtes d’abandon sont mises à jour pour refléter l’emplacement actuel du caret.

## <a name="displaying-and-updating-the-navigation-bar"></a>Affichage et mise à jour de la barre de navigation
 Pour prendre en charge la barre de <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> navigation, <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> vous devez tirer une classe de la classe et mettre en œuvre la méthode. Lorsque votre service linguistique reçoit une <xref:Microsoft.VisualStudio.Package.LanguageService> fenêtre de code, la classe de base instantanément le <xref:Microsoft.VisualStudio.Package.CodeWindowManager>, qui contient l’objet <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> représentant la fenêtre de code. L’objet <xref:Microsoft.VisualStudio.Package.CodeWindowManager> reçoit alors <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> un nouvel objet. La <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> méthode <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> obtient un objet. Si vous retournez <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> une instance <xref:Microsoft.VisualStudio.Package.CodeWindowManager> de <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> votre classe, les appels <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> de votre [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] méthode pour remplir les listes internes et transmet votre objet au gestionnaire de barre déroulant. Le gestionnaire de barre de dépôt, <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.SetDropdownBar%2A> à <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> son tour, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar> appelle la méthode sur votre objet pour établir l’objet qui détient les deux barres de dépôt.

 Lorsque le caret <xref:Microsoft.VisualStudio.Package.LanguageService.OnIdle%2A> se déplace, la méthode appelle la <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> méthode. La <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> méthode de <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> base <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> appelle la méthode de votre classe pour mettre à jour l’état de la barre de navigation. Vous passez un <xref:Microsoft.VisualStudio.Package.DropDownMember> ensemble d’objets à cette méthode. Chaque objet représente une entrée dans le drop-down.

## <a name="the-contents-of-the-navigation-bar"></a>Le contenu de la barre de navigation
 La barre de navigation contient habituellement une liste de types et une liste de membres. La liste des types comprend tous les types disponibles dans le fichier source actuel. Les noms de type incluent les informations complètes de l’espace de nom. Voici un exemple de code C avec deux types :

```csharp
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

 La liste de `TestLanguagePackage.TestLanguageService` `TestLanguagePackage.TestLanguageService.Tokens`type s’affichera et .

 La liste des membres affiche les membres disponibles du type qui est sélectionné dans la liste des types. En utilisant l’exemple `TestLanguagePackage.TestLanguageService` de code ci-dessus, si c’est `tokens` `serviceName`le type qui est sélectionné, la liste des membres contiendrait les membres privés et . La structure `Token` interne n’est pas affichée.

 Vous pouvez implémenter la liste des membres pour rendre le nom d’un membre audacieux lorsque le caret est placé à l’intérieur. Les membres peuvent également être affichés dans un texte grisé, ce qui indique qu’ils ne sont pas dans la portée où le caret est actuellement positionné.

## <a name="enabling-support-for-the-navigation-bar"></a>Permettre le soutien à la barre de navigation
 Pour activer le support de la `ShowDropdownBarOption` barre <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> de `true`navigation, vous devez définir le paramètre de l’attribut à . Ce paramètre définit la propriété <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A>. Pour prendre en charge la <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> barre de <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> navigation, <xref:Microsoft.VisualStudio.Package.LanguageService> vous devez implémenter l’objet dans la méthode de la classe.

 Dans votre mise <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> en œuvre de la méthode, si la <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> propriété est définie à `true`, vous pouvez retourner un <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> objet. Si vous ne retournez pas l’objet, la barre de navigation n’est pas affichée.

 L’option pour afficher la barre de navigation peut être définie par l’utilisateur, il est donc possible pour ce contrôle d’être réinitialisé pendant que la vue de l’éditeur est ouverte. L’utilisateur doit fermer et rouvrir la fenêtre de l’éditeur avant que le changement n’ait lieu.

## <a name="implementing-support-for-the-navigation-bar"></a>Mise en œuvre du soutien à la barre de navigation
 La <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> méthode prend deux listes (une pour chaque décrochage) et deux valeurs représentant la sélection actuelle dans chaque liste. Les listes et les valeurs de sélection <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> peuvent être `true` mises à jour, auquel cas la méthode doit revenir pour indiquer que les listes ont changé.

 Au fur et à mesure que la sélection change dans les types d’abandon, la liste des membres doit être mise à jour pour refléter le nouveau type. Ce qui est indiqué dans la liste des membres peut être soit :

- La liste des membres pour le type actuel.

- Tous les membres disponibles dans le fichier source, mais avec tous les membres pas dans le type actuel affiché dans le texte grisé. L’utilisateur peut toujours sélectionner les membres grisés, de sorte qu’ils peuvent être utilisés pour une navigation rapide, mais la couleur indique qu’ils ne font pas partie du type actuellement sélectionné.

  Une mise <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> en œuvre de la méthode effectue généralement les étapes suivantes :

1. Obtenez une liste des déclarations actuelles pour le fichier source.

     Il existe un certain nombre de façons de remplir les listes. Une approche consiste à créer une méthode <xref:Microsoft.VisualStudio.Package.LanguageService> personnalisée sur <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> votre version de la classe qui appelle la méthode avec une raison personnalisée de portée qui renvoie une liste de toutes les déclarations. Une autre approche pourrait <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> être d’appeler la méthode directement à partir de la <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> méthode avec la raison de l’analyse personnalisée. Une troisième approche pourrait consister à <xref:Microsoft.VisualStudio.Package.AuthoringScope> mettre en cache les déclarations <xref:Microsoft.VisualStudio.Package.LanguageService> de la classe <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> retournées par la dernière opération d’analyse complète de la classe et à les récupérer à partir de la méthode.

2. Remplissez ou mettez à jour la liste des types.

     Le contenu de la liste des types peut être mis à jour lorsque la source a changé ou si vous avez choisi de modifier le style texte des types en fonction de la position actuelle caret. Notez que cette position <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> est transmise à la méthode.

3. Déterminez le type à sélectionner dans la liste des types en fonction de la position actuelle de caret.

     Vous pouvez rechercher les déclarations qui ont été obtenues à l’étape 1 pour trouver le type qui entoure la position actuelle caret, puis rechercher la liste des types pour ce type pour déterminer son index dans la liste des types.

4. Remplissez ou mettez à jour la liste des membres en fonction du type sélectionné.

     La liste des membres reflète ce qui est actuellement affiché dans le décrochage des **Membres.** Le contenu de la liste des membres peut devoir être mis à jour si la source a changé ou si vous n’affichez que les membres du type sélectionné et le type sélectionné a changé. Si vous choisissez d’afficher tous les membres dans le fichier source, le style texte de chaque membre de la liste doit être mis à jour si le type actuellement sélectionné a changé.

5. Déterminez le membre à choisir dans la liste des membres en fonction du poste de soignant actuel.

     Rechercher les déclarations obtenues à l’étape 1 pour le membre qui contient la position actuelle de caret, puis rechercher la liste des membres pour que ce membre détermine son index dans la liste des membres.

6. Retour `true` si des modifications ont été apportées aux listes ou aux sélections dans l’une ou l’autre liste.
