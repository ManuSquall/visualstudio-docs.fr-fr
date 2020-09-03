---
title: Prise en charge de la barre de navigation dans un service de langage hérité | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80704865"
---
# <a name="support-for-the-navigation-bar-in-a-legacy-language-service"></a>Prise en charge de la barre de navigation dans un service de langage hérité
La barre de navigation en haut de la vue de l’éditeur affiche les types et les membres dans le fichier. Les types sont affichés dans la liste déroulante de gauche, et les membres s’affichent dans la liste déroulante de droite. Lorsque l’utilisateur sélectionne un type, le signe insertion est placé sur la première ligne du type. Lorsque l’utilisateur sélectionne un membre, le signe insertion est placé sur la définition du membre. Les zones de liste déroulante sont mises à jour pour refléter l’emplacement actuel du signe insertion.

## <a name="displaying-and-updating-the-navigation-bar"></a>Affichage et mise à jour de la barre de navigation
 Pour prendre en charge la barre de navigation, vous devez dériver une classe de la <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> classe et implémenter la <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> méthode. Lorsque votre service de langage reçoit une fenêtre de code, la <xref:Microsoft.VisualStudio.Package.LanguageService> classe de base instancie le <xref:Microsoft.VisualStudio.Package.CodeWindowManager> , qui contient l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> objet représentant la fenêtre de code. <xref:Microsoft.VisualStudio.Package.CodeWindowManager>Un nouvel objet est ensuite attribué à l’objet <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> . La <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> méthode obtient un <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> objet. Si vous retournez une instance de votre <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> classe, <xref:Microsoft.VisualStudio.Package.CodeWindowManager> appelle votre <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> méthode pour remplir les listes internes et passe votre <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> objet au gestionnaire de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] barres déroulantes. Le gestionnaire de barres déroulantes, à son tour, appelle la <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.SetDropdownBar%2A> méthode sur votre <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> objet pour établir l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar> objet qui contient les deux barres déroulantes.

 Lorsque le signe insertion se déplace, la <xref:Microsoft.VisualStudio.Package.LanguageService.OnIdle%2A> méthode appelle la <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> méthode. La méthode de base <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> appelle la <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> méthode dans votre <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> classe pour mettre à jour l’état de la barre de navigation. Vous transmettez un ensemble d' <xref:Microsoft.VisualStudio.Package.DropDownMember> objets à cette méthode. Chaque objet représente une entrée dans la liste déroulante.

## <a name="the-contents-of-the-navigation-bar"></a>Contenu de la barre de navigation
 La barre de navigation contient généralement une liste de types et une liste de membres. La liste des types comprend tous les types disponibles dans le fichier source actuel. Les noms de types incluent les informations complètes sur l’espace de noms. Voici un exemple de code C# avec deux types :

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

 La liste Type affiche `TestLanguagePackage.TestLanguageService` et `TestLanguagePackage.TestLanguageService.Tokens` .

 La liste membres affiche les membres disponibles du type sélectionné dans la liste types. À l’aide de l’exemple de code ci-dessus, si `TestLanguagePackage.TestLanguageService` est le type sélectionné, la liste des membres contient les membres privés `tokens` et `serviceName` . La structure interne `Token` n’est pas affichée.

 Vous pouvez implémenter la liste des membres pour mettre en gras le nom d’un membre lorsque le signe insertion est placé à l’intérieur de celui-ci. Les membres peuvent également être affichés dans du texte grisé, indiquant qu’ils ne se trouvent pas dans l’étendue où le signe insertion est actuellement positionné.

## <a name="enabling-support-for-the-navigation-bar"></a>Activation de la prise en charge de la barre de navigation
 Pour activer la prise en charge de la barre de navigation, vous devez affecter au `ShowDropdownBarOption` paramètre de l’attribut la valeur <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> `true` . Ce paramètre définit la propriété <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A>. Pour prendre en charge la barre de navigation, vous devez implémenter l' <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> objet dans la <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> méthode sur la <xref:Microsoft.VisualStudio.Package.LanguageService> classe.

 Dans votre implémentation de la <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> méthode, si la <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> propriété a la valeur `true` , vous pouvez retourner un <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> objet. Si vous ne retournez pas l’objet, la barre de navigation n’est pas affichée.

 L’option permettant d’afficher la barre de navigation peut être définie par l’utilisateur. il est donc possible de réinitialiser ce contrôle lorsque la vue de l’éditeur est ouverte. L’utilisateur doit fermer et rouvrir la fenêtre de l’éditeur pour que la modification ait lieu.

## <a name="implementing-support-for-the-navigation-bar"></a>Implémentation de la prise en charge de la barre de navigation
 La <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> méthode accepte deux listes (une pour chaque liste déroulante) et deux valeurs représentant la sélection actuelle dans chaque liste. Les listes et les valeurs de sélection peuvent être mises à jour. dans ce cas, la <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> méthode doit retourner `true` pour indiquer que les listes ont été modifiées.

 Lorsque la sélection change dans la liste déroulante types, la liste des membres doit être mise à jour pour refléter le nouveau type. Les éléments affichés dans la liste des membres peuvent être :

- Liste des membres du type actuel.

- Tous les membres disponibles dans le fichier source, mais avec tous les membres qui ne sont pas dans le type actuel affichés dans du texte grisé. L’utilisateur peut toujours sélectionner les membres grisés, afin qu’ils puissent être utilisés pour la navigation rapide, mais la couleur indique qu’ils ne font pas partie du type actuellement sélectionné.

  Une implémentation de la <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> méthode effectue généralement les étapes suivantes :

1. Obtient la liste des déclarations actuelles pour le fichier source.

     Il existe plusieurs façons de remplir les listes. Une approche consiste à créer une méthode personnalisée sur votre version de la <xref:Microsoft.VisualStudio.Package.LanguageService> classe qui appelle la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode avec une raison d’analyse personnalisée qui retourne une liste de toutes les déclarations. Une autre approche consiste à appeler la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode directement à partir de la <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> méthode avec la raison de l’analyse personnalisée. Une troisième approche peut consister à mettre en cache les déclarations de la <xref:Microsoft.VisualStudio.Package.AuthoringScope> classe retournée par la dernière opération d’analyse complète dans la <xref:Microsoft.VisualStudio.Package.LanguageService> classe et à récupérer celle-ci à partir de la <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> méthode.

2. Renseignez ou mettez à jour la liste des types.

     Le contenu de la liste des types peut être mis à jour lorsque la source a changé ou si vous avez choisi de modifier le style du texte des types en fonction de l’emplacement actuel du signe insertion. Notez que cette position est transmise à la <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> méthode.

3. Déterminez le type à sélectionner dans la liste des types en fonction de l’emplacement actuel du signe insertion.

     Vous pouvez rechercher les déclarations obtenues à l’étape 1 pour trouver le type qui englobe l’emplacement actuel du signe insertion, puis rechercher dans la liste des types ce type pour déterminer son index dans la liste des types.

4. Remplit ou met à jour la liste des membres en fonction du type sélectionné.

     La liste des membres reflète ce qui est actuellement affiché dans la liste déroulante **membres** . Le contenu de la liste des membres devra peut-être être mis à jour si la source a changé ou si vous affichez uniquement les membres du type sélectionné et que le type sélectionné a été modifié. Si vous choisissez d’afficher tous les membres dans le fichier source, le style de texte de chaque membre de la liste doit être mis à jour si le type actuellement sélectionné a changé.

5. Déterminez le membre à sélectionner dans la liste des membres en fonction de l’emplacement actuel du signe insertion.

     Recherchez dans les déclarations obtenues à l’étape 1 le membre qui contient l’emplacement actuel du signe insertion, puis recherchez dans la liste des membres de ce membre pour déterminer son index dans la liste des membres.

6. Retourne `true` si des modifications ont été apportées aux listes ou aux sélections dans l’une ou l’autre liste.
