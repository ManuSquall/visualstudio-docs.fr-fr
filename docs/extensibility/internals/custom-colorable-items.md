---
title: "&#201;l&#233;ments coloriable personnalis&#233;s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "propriétés"
  - "services de langage, les éléments coloriable personnalisés"
ms.assetid: b4d0ddee-c04b-48dc-ba82-f6068570cef0
caps.latest.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 24
---
# &#201;l&#233;ments coloriable personnalis&#233;s
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Vous pouvez remplacer la liste des types de colorisation, tels que les mots clés et des commentaires, en implémentant des éléments coloriable personnalisés dans le cadre de votre service de langage.  
  
## Paramètres utilisateur des propriétés  
 Vous pouvez afficher le **polices et couleurs** boîte de dialogue en sélectionnant **Options** sur la **outils** menu, puis en sélectionnant **polices et couleurs** sous **environnement**. Lorsque vous sélectionnez un affichage, tel que **éditeur de texte** ou **fenêtre commande**, le **Afficher les éléments** zone de liste affiche tous les éléments coloriable pour qui s’affichent. Vous pouvez afficher et modifier la police, taille, couleur de premier plan et couleur d’arrière\-plan pour chaque élément coloriable. Vos choix sont stockées dans un cache dans le Registre et accessible par le nom de l’élément coloriable.  
  
## Présentation des propriétés  
 Étant donné que l’IDE gère les substitutions par l’utilisateur d’éléments pouvant être en couleur dans le **polices et couleurs** boîte de dialogue, vous devez uniquement fournir chaque élément coloriable personnalisé avec un nom. Ce nom est ce qui apparaît dans les **Afficher les éléments** liste. Les éléments pouvant être en couleur apparaissent dans l’ordre alphabétique. Pour regrouper des éléments coloriable personnalisé de votre service de langage, vous pouvez commencer chaque nom avec le nom de votre langage, par exemple **NewLanguage \- commentaire** et **NewLanguage \- mot clé**.  
  
> [!CAUTION]
>  Vous devez inclure le nom du langage dans le nom de l’élément coloriable pour éviter les conflits avec des noms d’élément coloriable existants. Si vous modifiez le nom de l’un de vos éléments coloriable pendant le développement, vous devez réinitialiser le cache a été créé la première fois que vos éléments coloriable ont eu accès. Vous pouvez réinitialiser le cache expérimental avec l’outil CreateExpInstance, qui est installé avec le SDK de Visual Studio, généralement dans le répertoire  
>   
>  **C:\\Program fichiers \(x86\) \\Microsoft Visual Studio 14.0\\VSSDK\\VisualStudioIntegration\\Tools\\Bin**  
>   
>  Pour réinitialiser le cache, appelez `CreateExpInstance /Reset`. Pour plus d’informations sur CreateExpInstance, consultez la page [Utilitaire de CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md).  
  
 Le premier élément dans la liste de propriétés n’est jamais référencé. Le premier élément correspond à un index de l’élément coloriable 0, et [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fournit toujours les couleurs de texte par défaut et les attributs de cet élément. Le moyen le plus simple de traiter cet élément non référencé consiste à fournir un élément coloriable espace réservé comme le premier élément dans la liste.  
  
## Implémentation des éléments coloriable personnalisés  
  
1.  Définir ce qui doit être colorisé dans votre langage, par exemple \(mot clé\), opérateur et identificateur.  
  
2.  Créez une énumération de ces éléments coloriable.  
  
3.  Associer les types de jetons retournés par un analyseur ou le moteur d’analyse avec les valeurs énumérées.  
  
     Par exemple, les valeurs représentant les types de jetons peuvent être les mêmes valeurs dans l’énumération d’éléments coloriable personnalisé.  
  
4.  Dans votre implémentation de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> méthode dans votre <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> d’objet, de remplir la liste des attributs avec les valeurs de votre énumération éléments coloriable personnalisé correspondant à ces types de jeton retournés par le scanneur ou l’analyseur.  
  
5.  Dans la même classe qui implémente le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> de l’interface, implémentez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> interface et ses deux méthodes, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> et <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>.  
  
6.  Implémentez l'interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>.  
  
7.  Si vous souhaitez prendre en charge les valeurs de couleur 24 bits ou élevé, vous devez également implémenter la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interface.  
  
8.  Dans l’objet de service de langage, créer une liste qui contient votre <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> objets, un pour chaque élément coloriable votre analyseur ou l’analyseur peut identifier.  
  
     Vous pouvez accéder à chaque élément de la liste à l’aide de la valeur correspondante de l’énumération des éléments coloriable personnalisé. Utilisez les valeurs d’énumération en tant qu’index dans la liste. Le premier élément de la liste n’est jamais accessible, car il correspond au texte par défaut de style qui [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] toujours gère lui\-même. Pour cela, vous pouvez compenser en insérant un élément coloriable espace réservé au début de la liste.  
  
9. Dans votre implémentation de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> \(méthode\), retourner le nombre d’éléments dans votre liste coloriable personnalisé.  
  
10. Dans votre implémentation de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> \(méthode\), retourner l’élément coloriable demandé à partir de votre liste.  
  
 Pour obtenir un exemple montrant comment implémenter les <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> et <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> les interfaces, consultez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>.  
  
## Voir aussi  
 [Modèle d’un Service de langage hérité](../../extensibility/internals/model-of-a-legacy-language-service.md)   
 [Couleurs de syntaxe dans les éditeurs personnalisés](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [Couleurs de syntaxe dans un Service de langage hérité](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [L'implémentation de la coloration de syntaxe](../../extensibility/internals/implementing-syntax-coloring.md)   
 [Comment : utiliser des éléments coloriable intégrés](../../extensibility/internals/how-to-use-built-in-colorable-items.md)