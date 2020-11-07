---
title: Procédure pas à pas d’analyse du code managé pour les erreurs de code | Microsoft Docs
ms.date: 01/29/2018
description: Découvrez comment utiliser l’analyse du code hérité pour analyser les assemblys de code managé .NET. Consultez Comment vérifier les défauts et la conformité avec les règles de conception de .NET.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis [Visual Studio]
- managed code, analyzing
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 7e862b176ab396999d3504e19c4de9a5c407b266
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94349020"
---
# <a name="walkthrough-use-static-code-analysis-to-find-code-defects"></a>Procédure pas à pas : utiliser l’analyse statique du code pour rechercher les erreurs de code

Dans cette procédure pas à pas, vous allez analyser un projet managé pour les erreurs de code à l’aide de l’analyse du code hérité.

Cet article vous guide tout au long du processus d’utilisation de l’analyse héritée pour analyser vos assemblys de code managé .NET en conformité avec les règles de conception de .NET.

## <a name="create-a-class-library"></a>Créer une bibliothèque de classes

1. Ouvrez Visual Studio et créez un nouveau projet à partir du modèle **bibliothèque de classes (.NET Framework)** .

1. Nommez le projet **CodeAnalysisManagedDemo**.

1. Une fois le projet créé, ouvrez le fichier *Class1.cs* .

1. Remplacez le texte existant dans Class1.cs par le code suivant :

   ```csharp
   using System;

   namespace testCode
   {
       public class demo : Exception
       {
           public static void Initialize(int size) { }
           protected static readonly int _item;
           public static int item { get { return _item; } }
       }
   }
   ```

1. Enregistrez le fichier Class1.cs.

## <a name="analyze-the-project-for-code-defects"></a>Analyser le projet pour les erreurs de code

1. Sélectionnez le projet CodeAnalysisManagedDemo dans **Explorateur de solutions**.

2. Dans le menu **Projet** , cliquez sur **Propriétés**.

   La page de propriétés CodeAnalysisManagedDemo s’affiche.

3. Choisissez l’onglet **analyse du code** .

::: moniker range="vs-2017"

4. Assurez-vous que l’option **activer l’analyse du code sur la build** est sélectionnée.

5. Dans la liste déroulante **exécuter cet ensemble de règles** , sélectionnez **toutes les règles Microsoft**.

::: moniker-end

::: moniker range=">=vs-2019"

4. Assurez-vous que l’option **exécuter sur la build** est sélectionnée dans la section **analyseurs binaires** .

5. Dans la liste déroulante **règles actives** , sélectionnez **toutes les règles Microsoft**.

::: moniker-end

6. Dans le menu **fichier** , cliquez sur **enregistrer les éléments sélectionnés** , puis fermez les pages de propriétés.

7. Dans le menu **générer** , cliquez sur **générer CodeAnalysisManagedDemo**.

    Les avertissements de génération de projet CodeAnalysisManagedDemo s’affichent dans les fenêtres de **liste d’erreurs** et de **sortie** .

## <a name="correct-the-code-analysis-issues"></a>Corriger les problèmes liés à l’analyse du code

1. Dans le menu **affichage** , choisissez **liste d’erreurs**.

    En fonction du profil de développeur que vous avez choisi, vous devrez peut-être pointer sur **autres fenêtres** dans le menu **affichage** , puis choisir **liste d’erreurs**.

1. Dans l’ **Explorateur de solutions** , choisissez **Afficher tous les fichiers**.

1. Développez le nœud Propriétés, puis ouvrez le fichier *AssemblyInfo.cs* .

1. Utilisez les conseils suivants pour corriger les avertissements :

   [CA1014 : marquer les assemblys avec CLSCompliantAttribute](/dotnet/fundamentals/code-analysis/quality-rules/ca1014): ajoutez le code `[assembly: CLSCompliant(true)]` à la fin du fichier AssemblyInfo.cs.

   [CA1032 : implémenter des constructeurs d’exception standard](/dotnet/fundamentals/code-analysis/quality-rules/ca1032): ajoutez le constructeur `public demo (String s) : base(s) { }` à la classe `demo` .

   [CA1032 : implémenter des constructeurs d’exception standard](/dotnet/fundamentals/code-analysis/quality-rules/ca1032): ajoutez le constructeur `public demo (String s, Exception e) : base(s, e) { }` à la classe `demo` .

   [CA1032 : implémenter des constructeurs d’exception standard](/dotnet/fundamentals/code-analysis/quality-rules/ca1032): ajoutez le constructeur `protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { }` à la démonstration de classe. Vous devez également ajouter une `using` instruction pour <xref:System.Runtime.Serialization?displayProperty=fullName> .

   [CA1032 : implémenter des constructeurs d’exception standard](/dotnet/fundamentals/code-analysis/quality-rules/ca1032): ajoutez le constructeur `public demo () : base() { }` à la classe `demo` .

   [CA1709 : la casse des identificateurs doit être correcte](../code-quality/ca1709.md): remplacez la casse de l’espace de noms `testCode` par `TestCode` .

   [CA1709 : la casse des identificateurs doit être correcte](../code-quality/ca1709.md): remplacez le nom du membre par `Demo` .

   [CA1709 : la casse des identificateurs doit être correcte](../code-quality/ca1709.md): remplacez le nom du membre par `Item` .

   [CA1710 : les identificateurs doivent avoir un suffixe correct](/dotnet/fundamentals/code-analysis/quality-rules/ca1710): remplacez le nom de la classe et ses constructeurs par `DemoException` .

   [CA2237 : Marquez les types ISerializable avec SerializableAttribute](/dotnet/fundamentals/code-analysis/quality-rules/ca2237): ajoutez l' `[Serializable ()]` attribut à la classe `demo` .

   [CA2210 : les assemblys doivent avoir des noms forts valides](../code-quality/ca2210.md): Sign’CodeAnalysisManagedDemo’avec une clé de nom fort :

   1. Dans le menu **projet** , choisissez **Propriétés de CodeAnalysisManagedDemo**.

      Les propriétés du projet s’affichent.

   1. Choisissez l'onglet **Signature** .

   1. Activez la case à cocher **signer l’assembly** .

   1. Dans la liste **choisir un fichier de clé de nom de chaîne** , sélectionnez **\<New>** .

      La boîte de dialogue **Créer une clé de nom fort** s'affiche.

   1. Pour le **nom du fichier de clé** , entrez **TestKey**.

   1. Entrez un mot de passe, puis choisissez **OK**.

   1. Dans le menu **fichier** , sélectionnez **enregistrer les éléments sélectionnés** , puis fermez les pages de propriétés.

   Une fois toutes les modifications terminées, le fichier Class1.cs doit ressembler à ce qui suit :

   ```csharp
   using System;
   using System.Runtime.Serialization;

   namespace TestCode
   {
       [Serializable()]
       public class DemoException : Exception
       {
           public DemoException () : base() { }
           public DemoException(String s) : base(s) { }
           public DemoException(String s, Exception e) : base(s, e) { }
           protected DemoException(SerializationInfo info, StreamingContext context) : base(info, context) { }

           public static void Initialize(int size) { }
           protected static readonly int _item;
           public static int Item { get { return _item; } }
       }
   }
   ```

1. Regénérez le projet.

## <a name="exclude-code-analysis-warnings"></a>Exclure les avertissements d’analyse du code

1. Pour chacun des avertissements restants, procédez comme suit :

    1. Sélectionnez l’avertissement dans la **liste d’erreurs**.

    1. Dans le menu contextuel (menu contextuel), choisissez **supprimer**  >  **dans le fichier de suppression**.

1. Regénérez le projet.

     Le projet est généré sans avertissements ou erreurs.

## <a name="see-also"></a>Voir aussi

[Analyse du code pour le code managé](../code-quality/code-analysis-for-managed-code-overview.md)
