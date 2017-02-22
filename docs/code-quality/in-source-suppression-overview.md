---
title: "Vue d’ensemble de la suppression &#224; la source | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "suppression de la source, analyse du code"
  - "analyse du code, suppression de la source"
ms.assetid: f1a2dc6a-a9eb-408c-9078-2571e57d207d
caps.latest.revision: 40
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 40
---
# Vue d’ensemble de la suppression &#224; la source
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La suppression à la source est la capacité de supprimer ou d'ignorer des violations d'analyse du code dans le code managé en ajoutant l'attribut **SuppressMessage** aux segments de code à l'origine des violations.  L'attribut **SuppressMessage** est un attribut conditionnel qui est uniquement inclus dans les métadonnées IL \(Intermediate Language\) de votre assembly de code managé si le symbole de compilation CODE\_ANALYSIS est défini à la compilation.  
  
 En C\+\+\/CLI, utilisez les macros CA\_SUPPRESS\_MESSAGE ou CA\_GLOBAL\_SUPPRESS\_MESSAGE dans le fichier d'en\-tête pour ajouter l'attribut.  
  
 Vous ne devez pas utiliser de suppressions à la source sur les versions release afin d'éviter l'expédition par erreur des métadonnées de suppression à la source.  À cause du coût de traitement de la suppression à la source, les performances de votre application peuvent également être affectées par l'ajout des métadonnées de suppression à la source.  
  
> [!NOTE]
>  Vous n'avez pas à coder vous\-même à la main ces attributs.  Pour plus d'informations, consultez [Comment : supprimer des avertissements à l’aide de l’élément de menu](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md).  L'élément de menu n'est pas disponible pour le code C\+\+.  
  
## Attribut SuppressMessage  
 Lorsque vous cliquez avec le bouton droit sur un avertissement d'analyse du code dans la **Liste d'erreurs**, puis que vous cliquez sur **Supprimer les messages**, un attribut **SuppressMessage** est ajouté à votre code ou au fichier des suppressions globales du projet.  
  
 L'attribut **SuppressMessage** a le format suivant :  
  
```vb  
<Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")>  
```  
  
```c#  
[Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")]  
  
```  
  
 \[C\+\+\]  
  
```  
CA_SUPPRESS_MESSAGE("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")  
  
```  
  
 Où :  
  
-   **Catégorie de règle** \- Catégorie dans laquelle la règle est définie.  Pour plus d'informations sur les catégories de règles d'analyse du code, consultez [Analyse du code pour les avertissements liés au code managé](../code-quality/code-analysis-for-managed-code-warnings.md).  
  
-   **ID de règle** \- Identificateur de la règle.  Un nom court et un nom long sont pris en charge pour l'ID de règle.  Le nom court est CAXXXX, le nom long est CAXXXX:FriendlyTypeName.  
  
-   **Justification** \- Texte utilisé pour documenter la raison de la suppression du message.  
  
-   **Identificateur de message** \- Identificateur unique d'un problème pour chaque message.  
  
-   **Portée** \- Cible sur laquelle l'avertissement est supprimé.  Si la cible n'est pas spécifiée, elle a pour valeur la cible de l'attribut.  Les portées prises en charge sont les suivantes :  
  
    -   Module  
  
    -   Espace de noms  
  
    -   Ressource  
  
    -   Type  
  
    -   Membre  
  
-   **Cible** \- Identificateur utilisé pour spécifier la cible sur laquelle l'avertissement est supprimé.  Il doit contenir un nom d'élément complet.  
  
## Utilisation de SuppressMessage  
 Les avertissements d'analyse du code sont supprimés au niveau auquel une instance de l'attribut **SuppressMessage** est appliquée.  Le but de ceci est d'associer étroitement les informations de suppression au code où la violation se produit.  
  
 Le type de suppression courant inclut la catégorie de règle et un identificateur de règle qui contient une représentation explicite facultative du nom de la règle.  Par exemple :  
  
 `[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`  
  
 S'il existe des motifs sérieux liés aux performances pour réduire les métadonnées de suppression à la source, le nom de la règle lui\-même peut être ignoré.  La catégorie de règle et son ID de règle constituent un identificateur de règle unique suffisant.  Par exemple :  
  
 `[SuppressMessage("Microsoft.Design", "CA1039")]`  
  
 Ce format n'est pas recommandé à cause des problèmes de facilité de maintenance.  
  
## Suppression de plusieurs violations dans un corps de méthode  
 Les attributs ne peuvent être appliqués qu'à une méthode et ne peuvent pas être incorporés dans le corps de la méthode.  Toutefois, vous pouvez spécifier l'identificateur comme ID de message pour distinguer plusieurs occurrences d'une violation dans une méthode.  
  
 [!code-cpp[InSourceSuppression#1](../code-quality/codesnippet/CPP/in-source-suppression-overview_1.cpp)]
 [!code-vb[InSourceSuppression#1](../code-quality/codesnippet/VisualBasic/in-source-suppression-overview_1.vb)]
 [!code-cs[InSourceSuppression#1](../code-quality/codesnippet/CSharp/in-source-suppression-overview_1.cs)]  
  
## Code généré  
 Les compilateurs de code managé et quelques outils tiers génèrent le code pour faciliter un développement rapide.  Le code généré par le compilateur qui apparaît dans les fichiers sources est habituellement marqué avec l'attribut **GeneratedCodeAttribute**.  
  
 Vous pouvez choisir de supprimer ou non les avertissements d'analyse du code et les erreurs pour le code généré.  Pour plus d'informations sur la suppression de tels avertissements et erreurs, consultez [Comment : supprimer les avertissements pour du code généré](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md).  
  
 Notez que l'analyse du code ignore **GeneratedCodeAttribute** lorsqu'il s'applique à un assembly entier ou un paramètre seul.  Ces situations se produisent rarement.  
  
## Suppressions au niveau global  
 L'outil d'analyse du code managé examine les attributs **SuppressMessage** qui sont appliqués au niveau de l'assembly, du module, du type, du membre ou du paramètre.  Il déclenche également des violations pour les ressources et les espaces de noms.  Ces violations doivent être appliquées au niveau global du module ; elles ont une portée limitée et sont ciblées.  Par exemple, le message suivant supprime une violation d'espace de noms :  
  
 `[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`  
  
> [!NOTE]
>  Lorsque vous supprimez un avertissement avec une portée d'espace de noms, il supprime l'avertissement par rapport à l'espace de noms lui\-même.  Il ne supprime pas l'avertissement par rapport à des types dans l'espace de noms.  
  
 Toute suppression peut être exprimée en spécifiant une portée explicite.  Ces suppressions doivent avoir lieu au niveau global.  Vous ne pouvez pas spécifier une suppression au niveau membre en décorant un type.  
  
 Les suppressions au niveau global constituent le seul moyen de supprimer des messages qui font référence au code généré par le compilateur qui n'est pas mappé avec le code source utilisateur explicitement fourni.  Par exemple, le code suivant supprime une violation concernant un constructeur émis par le compilateur :  
  
 `[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`  
  
> [!NOTE]
>  La cible contient toujours le nom d'élément complet.  
  
## Fichier de suppression globale  
 Le fichier de suppression globale conserve les suppressions de niveau global ou qui ne spécifient pas de cible.  Par exemple, les suppressions de violations au niveau assembly sont enregistrées dans ce fichier.  En outre, certaines suppressions ASP.NET sont stockées dans ce fichier parce que les paramètres de niveau de projet ne sont pas disponibles pour la forme code\-behind.  Une suppression globale est créée et ajoutée à votre projet la première fois que vous sélectionnez l'option **Dans le fichier de suppression du projet** de la commande **Supprimer les messages** dans la fenêtre Liste d'erreurs.  Pour plus d'informations, consultez [Comment : supprimer des avertissements à l’aide de l’élément de menu](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md).  
  
## Voir aussi  
 <xref:System.Diagnostics.CodeAnalysis>