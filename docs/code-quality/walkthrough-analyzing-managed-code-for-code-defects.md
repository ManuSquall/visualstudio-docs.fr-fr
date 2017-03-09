---
title: "Proc&#233;dure pas &#224; pas&#160;: analyse du code manag&#233; pour les erreurs de code | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "analyse du code, procédures pas à pas"
  - "code managé, analyse"
  - "outil d’analyse du code, procédures pas à pas"
ms.assetid: 22b99f49-1924-4fb5-a421-c8b23e5d5cd4
caps.latest.revision: 45
caps.handback.revision: 45
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Proc&#233;dure pas &#224; pas&#160;: analyse du code manag&#233; pour les erreurs de code
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dans cette procédure pas à pas, vous analysez un projet managé pour les erreurs de code à l’aide de l’outil d’analyse de code.  
  
 Cette procédure pas à pas vous guidera tout au long du processus d’utilisation de l’analyse du code pour analyser les assemblys de code managé .NET pour la conformité avec les instructions de conception de Microsoft .NET Framework.  
  
 Dans cette procédure pas à pas, vous :  
  
-   Analyser et corriger les avertissements d’erreur de code.  
  
## <a name="prerequisites"></a>Prérequis  
  
-   [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)].  
  
## <a name="create-a-class-library"></a>Créer une bibliothèque de classes  
  
#### <a name="to-create-a-class-library"></a>Pour créer une bibliothèque de classes  
  
1.  Sur le **fichier** menu [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], cliquez sur **nouveau** puis **projet**.  
  
2.  Dans la **Nouveau projet** boîte de dialogue **Types de projet**, cliquez sur **Visual C#**.  
  
3.  Sous **modèles**, sélectionnez **bibliothèque de classes**.  
  
4.  Dans le **nom** zone de texte, tapez **CodeAnalysisManagedDemo** puis **OK**.  
  
5.  Une fois le projet créé, ouvrez le fichier Class1.cs.  
  
6.  Remplacez le texte existant dans Class1.cs par le code suivant :  
  
     `//CodeAnalysisManagedDemo //Class1.cs using System;  namespace testCode {          public class demo : Exception     {                  public static void Initialize(int size) { }         protected static readonly int _item;         public static int item { get { return _item; } }     } }`  
  
7.  Enregistrez le fichier Class1.cs.  
  
## <a name="analyze-the-project"></a>Analyser le projet  
  
#### <a name="to-analyze-a-managed-project-for-code-defects"></a>Pour analyser un projet managé pour les erreurs de code  
  
1.  Sélectionnez le projet CodeAnalysisManagedDemo dans **l’Explorateur de solutions**.  
  
2.  Sur le **projet** menu, cliquez sur **propriétés**.  
  
     La page de propriétés CodeAnalysisManagedDemo s’affiche.  
  
3.  Cliquez sur **CodeAnalysis**.  
  
4.  Assurez-vous que  **Activer l’analyse du Code sur la Build (définit la constante CODE_ANALYSIS**) est activée.  
  
5.  À partir de la **exécuter cet ensemble de règles** la liste déroulante, sélectionnez **toutes les règles Microsoft**.  
  
6.  Sur le **fichier** menu, cliquez sur **Enregistrer les éléments sélectionnés**, puis fermez les pages de propriétés ManagedDemo.  
  
7.  Sur le **créer** menu, cliquez sur **Générer ManagedDemo**.  
  
     Les avertissements de build du projet CodeAnalysisManagedDemo sont signalés dans les **l’analyse du Code** et **sortie** windows.  
  
     Si le **l’analyse du Code** fenêtre est absente, sur le **analyser** menu, choisissez **Windows** puis **Choisissez analyse du Code**.  
  
## <a name="correct-the-code-analysis-issues"></a>Corriger les problèmes d’analyse de Code  
  
#### <a name="to-correct-code-analysis-rule-violations"></a>Pour corriger les violations de règles code analysis  
  
1.  Sur le **vue** menu, cliquez sur **liste d’erreurs**.  
  
     Selon le profil de développeur que vous avez choisi, vous devez pointer vers **autres fenêtres** sur la **vue** menu, puis sur **liste d’erreurs**.  
  
2.  Dans **l’Explorateur de solutions**, cliquez sur **Afficher tous les fichiers**.  
  
3.  Ensuite, développez le nœud Propriétés, puis ouvrez le fichier AssemblyInfo.cs.  
  
4.  Pour corriger les avertissements, utilisez les éléments suivants :  
  
-   [CA1014 : Marquer les assemblys avec CLSCompliantAttribute](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md): Microsoft.Design : 'demo' doit être marqué avec CLSCompliantAttribute et sa valeur doit être true.  
  
    -   Ajoutez le code `using``System;` dans le fichier AssemblyInfo.cs.  
  
         Ensuite, ajoutez le code `[assembly: CLSCompliant(true)]` à la fin du fichier AssemblyInfo.cs.  
  
         Regénérez le projet.  
  
-   [CA1032 : Implémenter des constructeurs d’exception standard](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design : ajoutez le constructeur suivant à cette classe : public demo (String)  
  
    -   Ajoutez le constructeur `public demo (String s) : base(s) { }` à la classe `demo`.  
  
-   [CA1032 : Implémenter des constructeurs d’exception standard](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design : ajoutez le constructeur suivant à cette classe : public demo (String, Exception)  
  
    -   Ajoutez le constructeur `public demo (String s, Exception e) : base(s, e) { }` à la classe `demo`.  
  
-   [CA1032 : Implémenter des constructeurs d’exception standard](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design : ajoutez le constructeur suivant à cette classe : protected demo (SerializationInfo, StreamingContext)  
  
    -   Ajoutez le code `using System.Runtime.Serialization;` au début du fichier Class1.cs.  
  
         Ensuite, ajoutez le constructeur `protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { } to the class demo.`  
  
         Regénérez le projet.  
  
-   [CA1032 : Implémenter des constructeurs d’exception standard](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design : ajoutez le constructeur suivant à cette classe : public demo()  
  
    -   Ajoutez le constructeur `public demo () : base() { }` à la classe `demo`**.**  
  
         Regénérez le projet.  
  
-   [CA1709 : La casse des identificateurs doivent être correcte](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming : corrigez la casse du nom de l’espace de noms « testCode » en le redéfinissant sur « TestCode ».  
  
    -   Remplacez la casse de l’espace de noms `testCode` à `TestCode`.  
  
-   [CA1709 : La casse des identificateurs doivent être correcte](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming : corrigez la casse du nom de type « demo » en le redéfinissant sur « Demo ».  
  
    -   Modifier le nom du membre à `Demo`.  
  
-   [CA1709 : La casse des identificateurs doivent être correcte](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming : corrigez la casse du nom de membre « item » en le redéfinissant sur « Item ».  
  
    -   Modifier le nom du membre à `Item`.  
  
-   [CA1710 : Les identificateurs doivent porter un suffixe correct](../Topic/CA1710:%20Identifiers%20should%20have%20correct%20suffix.md): Microsoft.Naming : Renommez 'testCode.Demo qu’il se » se termine par « Exception ».  
  
    -   Modifier le nom de la classe et ses constructeurs à `DemoException`.  
  
-   [CA2210 : Les assemblys doivent porter des noms forts valides](../Topic/CA2210:%20Assemblies%20should%20have%20valid%20strong%20names.md): Signez 'ManagedDemo' avec une clé de nom fort.  
  
    -   Sur le **projet** menu, cliquez sur **Propriétés de ManagedDemo**.  
  
         Les propriétés du projet s’affichent.  
  
         Cliquez sur **signature**.  
  
         Sélectionnez le **signer l’assembly** case à cocher.  
  
         Dans la **Choisir un fichier de clé de nom fort** liste, sélectionnez **\< nouveau... >**.  
  
         Le **créer une clé de nom fort** boîte de dialogue s’affiche.  
  
         Dans le **nom de fichier de clé**, tapez TestKey.  
  
         Entrez un mot de passe, puis **OK**.  
  
         Sur le **fichier** menu, cliquez sur **Enregistrer les éléments sélectionnés**, puis fermez les pages de propriétés.  
  
         Regénérez le projet.  
  
-   [CA2237 : Marquer les types ISerializable avec SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md): Microsoft.Usage : ajoutez un attribut [Serializable] type 'demo' car ce type implémente ISerializable.  
  
    -   Ajouter la `[Serializable ()]` à la classe d’attribut `demo`.  
  
         Regénérez le projet.  
  
 Après avoir effectué les modifications, le fichier Class1.cs doit se présenter comme suit :  
  
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
  
1.  Pour chacun des avertissements restants, procédez comme suit :  
  
    1.  Dans la fenêtre analyse du Code, sélectionnez l’avertissement.  
  
    2.  Choisissez **Actions**, puis choisissez **Supprimer le Message**, puis choisissez **dans le fichier de Suppression de projet**.  
  
     Pour plus d’informations, consultez [Comment : supprimer les avertissements à l’aide de l’élément de Menu](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)  
  
2.  Regénérez le projet.  
  
     Le projet est généré sans erreurs ou avertissements.