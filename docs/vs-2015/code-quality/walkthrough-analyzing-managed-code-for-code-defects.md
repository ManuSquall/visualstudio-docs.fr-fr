---
title: 'Procédure pas à pas : Analyse du Code managé pour les erreurs de Code | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, walkthroughs
- managed code, analyzing
- code analysis tool, walkthroughs
ms.assetid: 22b99f49-1924-4fb5-a421-c8b23e5d5cd4
caps.latest.revision: 47
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 26d8412318efd2292fd0f5a0f0ef52fe36c7d06c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60116288"
---
# <a name="walkthrough-analyzing-managed-code-for-code-defects"></a>Procédure pas à pas : Analyse du code géré pour la recherche des défaillances du code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans cette procédure pas à pas, vous analysez un projet managé pour détecter les erreurs de code à l’aide de l’outil d’analyse de code.  
  
 Cette procédure pas à pas vous guidera tout au long du processus d’utilisation de l’analyse du code pour analyser les assemblys de code managé .NET pour la conformité avec les instructions de conception de Microsoft .NET Framework.  
  
 Dans cette procédure pas à pas, vous :  
  
- Analyser et corriger les avertissements d’erreur de code.  
  
## <a name="prerequisites"></a>Prérequis  
  
- [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)].  
  
## <a name="create-a-class-library"></a>Créer une bibliothèque de classes  
  
#### <a name="to-create-a-class-library"></a>Pour créer une bibliothèque de classes  
  
1. Sur le **fichier** menu de [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], cliquez sur **New** puis cliquez sur **projet**.  
  
2. Dans le **nouveau projet** boîte de dialogue **Types de projets**, cliquez sur **Visual C#** .  
  
3. Sous **modèles**, sélectionnez **bibliothèque de classes**.  
  
4. Dans le **nom** zone de texte, tapez **CodeAnalysisManagedDemo** puis cliquez sur **OK**.  
  
5. Une fois le projet est créé, ouvrez le fichier Class1.cs.  
  
6. Remplacez le texte existant dans le fichier Class1.cs par le code suivant :  
  
     `//CodeAnalysisManagedDemo //Class1.cs using System;  namespace testCode {          public class demo : Exception     {                  public static void Initialize(int size) { }         protected static readonly int _item;         public static int item { get { return _item; } }     } }`  
  
7. Enregistrez le fichier Class1.cs.  
  
## <a name="analyze-the-project"></a>Analyser le projet  
  
#### <a name="to-analyze-a-managed-project-for-code-defects"></a>Pour analyser un projet managé pour détecter les erreurs de code  
  
1. Sélectionnez le projet CodeAnalysisManagedDemo dans **l’Explorateur de solutions**.  
  
2. Dans le menu **Projet**, cliquez sur **Propriétés**.  
  
     La page de propriétés CodeAnalysisManagedDemo s’affiche.  
  
3. Cliquez sur **CodeAnalysis**.  
  
4. Assurez-vous que l’option **activer l’analyse du Code sur la Build (définit la constante CODE_ANALYSIS**) est activée.  
  
5. À partir de la **exécuter cet ensemble de règles** liste déroulante, sélectionnez **toutes les règles Microsoft**.  
  
6. Sur le **fichier** menu, cliquez sur **enregistrer les éléments sélectionnés**, puis fermez les pages de propriétés ManagedDemo.  
  
7. Sur le **Build** menu, cliquez sur **Générer ManagedDemo**.  
  
     Les avertissements de build du projet CodeAnalysisManagedDemo sont signalés dans le **analyse du Code** et **sortie** windows.  
  
     Si le **analyse du Code** fenêtre ne pas s’affiche, dans le **analyser** menu, choisissez **Windows** , puis **choisissez analyse du Code**.  
  
## <a name="correct-the-code-analysis-issues"></a>Corrigez les problèmes d’analyse de Code  
  
#### <a name="to-correct-code-analysis-rule-violations"></a>Pour corriger les violations des règles de code analysis  
  
1. Sur le **vue** menu, cliquez sur **liste d’erreurs**.  
  
     Selon le profil de développeur que vous avez choisi, vous devrez peut-être pointer vers **Windows autres** sur le **vue** menu, puis sur **liste d’erreurs**.  
  
2. Dans **l’Explorateur de solutions**, cliquez sur **afficher tous les fichiers**.  
  
3. Ensuite, développez le nœud Propriétés, puis ouvrez le fichier AssemblyInfo.cs.  
  
4. Pour corriger les avertissements, utilisez les éléments suivants :  
  
- [CA1014 : Marquer les assemblys avec CLSCompliantAttribute](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md): Microsoft.Design : « demo » doit être marqué avec CLSCompliantAttribute et sa valeur doit être true.  
  
  - Ajoutez le code `using``System;` dans le fichier AssemblyInfo.cs.  
  
       Ensuite, ajoutez le code `[assembly: CLSCompliant(true)]` à la fin du fichier AssemblyInfo.cs.  
  
       Regénérez le projet.  
  
- [CA1032 : Implémenter des constructeurs d’exception standard](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design : Ajoutez le constructeur suivant à cette classe : public demo (String)  
  
  - Ajoutez le constructeur `public demo (String s) : base(s) { }` à la classe `demo`.  
  
- [CA1032 : Implémenter des constructeurs d’exception standard](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design : Ajoutez le constructeur suivant à cette classe : public demo (String, Exception)  
  
  - Ajoutez le constructeur `public demo (String s, Exception e) : base(s, e) { }` à la classe `demo`.  
  
- [CA1032 : Implémenter des constructeurs d’exception standard](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design : Ajoutez le constructeur suivant à cette classe : protected demo (SerializationInfo, StreamingContext)  
  
  - Ajoutez le code `using System.Runtime.Serialization;` au début du fichier Class1.cs.  
  
       Ensuite, ajoutez le constructeur `protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { } to the class demo.`  
  
       Regénérez le projet.  
  
- [CA1032 : Implémenter des constructeurs d’exception standard](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design : Ajoutez le constructeur suivant à cette classe : public demo()  
  
  - Ajoutez le constructeur `public demo () : base() { }` à la classe `demo` **.**  
  
       Regénérez le projet.  
  
- [CA1709 : Identificateurs doivent être correcte](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming : Corrigez la casse du nom de l’espace de noms « testCode » en le redéfinissant sur « TestCode ».  
  
  - Modifier la casse de l’espace de noms `testCode` à `TestCode`.  
  
- [CA1709 : Identificateurs doivent être correcte](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming : Corrigez la casse du nom de type « demo » en le redéfinissant sur « Demo ».  
  
  - Modifier le nom du membre à `Demo`.  
  
- [CA1709 : Identificateurs doivent être correcte](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming : Corrigez la casse du nom de membre 'item' changez-la en 'Item'.  
  
  - Modifier le nom du membre à `Item`.  
  
- [CA1710 : Les identificateurs doivent avoir un suffixe correct](../code-quality/ca1710-identifiers-should-have-correct-suffix.md): Microsoft.Naming : Renommer « TestCode.Demo qu’il se » à la fin de 'Exception'.  
  
  - Modifier le nom de la classe et ses constructeurs à `DemoException`.  
  
- [CA2210 : Assemblys doivent avoir des noms forts valides](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md): Signez 'ManagedDemo' avec une clé de nom fort.  
  
  - Sur le **projet** menu, cliquez sur **ManagedDemo propriétés**.  
  
       Les propriétés de projet s’affichent.  
  
       Cliquez sur **signature**.  
  
       Sélectionnez le **signer l’assembly** case à cocher.  
  
       Dans le **choisir un fichier de clé de nom de chaîne** liste, sélectionnez  **\<nouveau... >** .  
  
       Le **créer une clé de nom fort** boîte de dialogue s’affiche.  
  
       Dans le **nom de fichier de clé**, tapez TestKey.  
  
       Entrez un mot de passe, puis activez **OK**.  
  
       Sur le **fichier** menu, cliquez sur **enregistrer les éléments sélectionnés**, puis fermez les pages de propriétés.  
  
       Regénérez le projet.  
  
- [CA2237 : Marquer les types ISerializable avec SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md): Microsoft.Usage : Ajoutez un attribut [Serializable] au type 'demo' car ce type implémente ISerializable.  
  
  - Ajouter le `[Serializable ()]` à la classe d’attribut `demo`.  
  
       Regénérez le projet.  
  
  Après avoir terminé les modifications, le fichier Class1.cs doit ressembler à ce qui suit :  
  
```  
//CodeAnalysisManagedDemo  
//Class1.cs  
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
  
## <a name="exclude-code-analysis-warnings"></a>Exclure les avertissements d’analyse du Code  
  
#### <a name="to-exclude-code-defect-warnings"></a>Pour exclure les avertissements d’erreur de code  
  
1. Pour chacun des avertissements restants, procédez comme suit :  
  
   1. Dans la fenêtre analyse du Code, sélectionnez l’avertissement.  
  
   2. Choisissez **Actions**, puis choisissez **supprimer le Message**, puis choisissez **dans le fichier de Suppression de projet**.  
  
      Pour plus d'informations, voir [Procédure : Supprimer les avertissements à l’aide de l’élément de Menu](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)  
  
2. Regénérez le projet.  
  
    Le projet est généré sans les avertissements ou erreurs.
