---
title: "Procédure pas à pas : Création d’un processeur de Directive personnalisé | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text templates, custom directive processors
- walkthroughs [text templates], directive processor
ms.assetid: b8f35a36-14e1-4467-8f5f-e01402af14d5
caps.latest.revision: 74
author: alancameronwills
ms.author: awills
manager: douge
translation.priority.ht:
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
ms.sourcegitcommit: eb2ab9d49cdeb1ed71da8ef67841f7796862dc30
ms.openlocfilehash: e27af2c3d824acd15a33cf1f452dcfa9ba2acf04
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-creating-a-custom-directive-processor"></a>Procédure pas à pas : création d'un processeur de directive personnalisé
*Processeurs de directive* fonctionnent en ajoutant du code pour le *classe de transformation générée*. Si vous appelez un *directive* d’un *modèle de texte*, le reste du code que vous écrivez dans votre modèle de texte peut faire appel aux fonctionnalités qu’elle fournit.  
  
 Vous pouvez écrire vos propres processeurs de directive personnalisés. Vous avez ainsi la possibilité de personnaliser vos modèles de texte. Pour créer un processeur de directive personnalisé, vous créez une classe qui hérite d’un <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor>ou <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>.</xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> </xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor>  
  
 Cette procédure pas à pas décrit notamment les tâches suivantes :  
  
-   Création d'un processeur de directive personnalisé  
  
-   Inscription du processeur de directive  
  
-   Test du processeur de directive  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure pas à pas, vous avez besoin des éléments suivants :  
  
-   Visual Studio 2010  
  
-   Kit de développement logiciel Visual Studio 2010  
  
## <a name="creating-a-custom-directive-processor"></a>Création d'un processeur de directive personnalisé  
 Dans cette procédure pas à pas, vous allez créer un processeur de directive personnalisé. Vous ajouterez une directive personnalisée qui lit un fichier XML, le stocke dans un <xref:System.Xml.XmlDocument>variable et l’expose via une propriété.</xref:System.Xml.XmlDocument> Dans la section « Test du processeur de directive », vous allez utiliser cette propriété dans un modèle de texte pour accéder au fichier XML.  
  
 L'appel à votre directive personnalisée se présente comme suit :  
  
 `<#@ CoolDirective Processor="CustomDirectiveProcessor" FileName="<Your Path>DocFile.xml" #>`  
  
 Le processeur de directive personnalisé ajoute la variable et la propriété à la classe de transformation générée. La directive que vous écrivez utilise les <xref:System.CodeDom>classes pour créer le code que le moteur ajoute à la classe de transformation générée.</xref:System.CodeDom> Le <xref:System.CodeDom>classes créent du code en Visual c# ou [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], selon le langage spécifié dans le `language` paramètre de la `template` directive.</xref:System.CodeDom> Le langage du processeur de directive et celui du modèle de texte qui accède à ce processeur ne doivent pas nécessairement correspondre.  
  
 Le code créé par la directive se présente comme suit :  
  
```c#  
private System.Xml.XmlDocument document0Value;  
  
public virtual System.Xml.XmlDocument Document0  
{  
  get  
  {  
    if ((this.document0Value == null))  
    {  
      this.document0Value = XmlReaderHelper.ReadXml(<FileNameParameterValue>);  
    }  
    return this.document0Value;  
  }  
}  
```  
  
```vb#  
Private document0Value As System.Xml.XmlDocument  
  
Public Overridable ReadOnly Property Document0() As System.Xml.XmlDocument  
    Get  
        If (Me.document0Value Is Nothing) Then  
            Me.document0Value = XmlReaderHelper.ReadXml(<FileNameParameterValue>)  
        End If  
        Return Me.document0Value  
    End Get  
End Property  
```  
  
#### <a name="to-create-a-custom-directive-processor"></a>Pour créer un processeur de directive personnalisé  
  
1.  Dans Visual Studio, créez un projet de bibliothèque de classes C# ou Visual Basic nommé CustomDP.  
  
    > [!NOTE]
    >  Si vous voulez installer le processeur de directive sur plusieurs ordinateurs, il est préférable d'utiliser un projet d'extension [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] (VSIX) et d'inclure un fichier .pkgdef dans l'extension. Pour plus d’informations, consultez [déploiement d’un processeur de Directive personnalisé](../modeling/deploying-a-custom-directive-processor.md).  
  
2.  Ajoutez des références aux assemblys suivants :  
  
    -   **Microsoft.VisualStudio.TextTemplating. \*.0**  
  
    -   **Microsoft.VisualStudio.TextTemplating.Interfaces. \*.0**  
  
3.  Remplacez le code dans **Class1** par le code suivant. Ce code définit une classe CustomDirectiveProcessor qui hérite de la <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor>classe et implémente les méthodes nécessaires.</xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor>  
  
    ```c#  
    using System;  
    using System.CodeDom;  
    using System.CodeDom.Compiler;  
    using System.Collections.Generic;  
    using System.Globalization;  
    using System.IO;  
    using System.Text;  
    using System.Xml;  
    using System.Xml.Serialization;  
    using Microsoft.VisualStudio.TextTemplating;  
  
    namespace CustomDP  
    {  
        public class CustomDirectiveProcessor : DirectiveProcessor  
        {  
            //this buffer stores the code that is added to the   
            //generated transformation class after all the processing is done   
            //---------------------------------------------------------------------  
            private StringBuilder codeBuffer;  
  
            //Using a Code Dom Provider creates code for the   
            //generated transformation class in either Visual Basic or C#.  
            //If you want your directive processor to support only one language, you  
            //can hard code the code you add to the generated transformation class.  
            //In that case, you do not need this field.  
            //--------------------------------------------------------------------------  
            private CodeDomProvider codeDomProvider;  
  
            //this stores the full contents of the text template that is being processed  
            //--------------------------------------------------------------------------  
            private String templateContents;  
  
            //These are the errors that occur during processing. The engine passes   
            //the errors to the host, and the host can decide how to display them,  
            //for example the the host can display the errors in the UI  
            //or write them to a file.  
            //---------------------------------------------------------------------  
            private CompilerErrorCollection errorsValue;  
            public new CompilerErrorCollection Errors  
            {  
                get { return errorsValue; }  
            }  
  
            //Each time this directive processor is called, it creates a new property.  
            //We count how many times we are called, and append "n" to each new  
            //property name. The property names are therefore unique.  
            //-----------------------------------------------------------------------------  
            private int directiveCount = 0;  
  
            public override void Initialize(ITextTemplatingEngineHost host)  
            {  
                //we do not need to do any initialization work  
            }  
  
            public override void StartProcessingRun(CodeDomProvider languageProvider, String templateContents, CompilerErrorCollection errors)  
            {  
                //the engine has passed us the language of the text template  
                //we will use that language to generate code later  
                //----------------------------------------------------------  
                this.codeDomProvider = languageProvider;  
                this.templateContents = templateContents;  
                this.errorsValue = errors;  
  
                this.codeBuffer = new StringBuilder();  
            }  
  
            //Before calling the ProcessDirective method for a directive, the   
            //engine calls this function to see whether the directive is supported.  
            //Notice that one directive processor might support many directives.  
            //---------------------------------------------------------------------  
            public override bool IsDirectiveSupported(string directiveName)  
            {  
                if (string.Compare(directiveName, "CoolDirective", StringComparison.OrdinalIgnoreCase) == 0)  
                {  
                    return true;  
                }  
                if (string.Compare(directiveName, "SuperCoolDirective", StringComparison.OrdinalIgnoreCase) == 0)  
                {  
                    return true;  
                }  
                return false;  
            }  
  
            public override void ProcessDirective(string directiveName, IDictionary<string, string> arguments)  
            {  
                if (string.Compare(directiveName, "CoolDirective", StringComparison.OrdinalIgnoreCase) == 0)  
                {  
                    string fileName;  
  
                    if (!arguments.TryGetValue("FileName", out fileName))  
                    {  
                        throw new DirectiveProcessorException("Required argument 'FileName' not specified.");  
                    }  
  
                    if (string.IsNullOrEmpty(fileName))  
                    {  
                        throw new DirectiveProcessorException("Argument 'FileName' is null or empty.");  
                    }  
  
                    //Now we add code to the generated transformation class.  
                    //This directive supports either Visual Basic or C#, so we must use the  
                    //System.CodeDom to create the code.  
                    //If a directive supports only one language, you can hard code the code.  
                    //--------------------------------------------------------------------------  
  
                    CodeMemberField documentField = new CodeMemberField();  
  
                    documentField.Name = "document" + directiveCount + "Value";  
                    documentField.Type = new CodeTypeReference(typeof(XmlDocument));  
                    documentField.Attributes = MemberAttributes.Private;  
  
                    CodeMemberProperty documentProperty = new CodeMemberProperty();  
  
                    documentProperty.Name = "Document" + directiveCount;  
                    documentProperty.Type = new CodeTypeReference(typeof(XmlDocument));  
                    documentProperty.Attributes = MemberAttributes.Public;  
                    documentProperty.HasSet = false;  
                    documentProperty.HasGet = true;  
  
                    CodeExpression fieldName = new CodeFieldReferenceExpression(new CodeThisReferenceExpression(), documentField.Name);  
                    CodeExpression booleanTest = new CodeBinaryOperatorExpression(fieldName, CodeBinaryOperatorType.IdentityEquality, new CodePrimitiveExpression(null));  
                    CodeExpression rightSide = new CodeMethodInvokeExpression(new CodeTypeReferenceExpression("XmlReaderHelper"), "ReadXml", new CodePrimitiveExpression(fileName));  
                    CodeStatement[] thenSteps = new CodeStatement[] { new CodeAssignStatement(fieldName, rightSide) };  
  
                    CodeConditionStatement ifThen = new CodeConditionStatement(booleanTest, thenSteps);  
                    documentProperty.GetStatements.Add(ifThen);  
  
                    CodeStatement s = new CodeMethodReturnStatement(fieldName);  
                    documentProperty.GetStatements.Add(s);  
  
                    CodeGeneratorOptions options = new CodeGeneratorOptions();  
                    options.BlankLinesBetweenMembers = true;  
                    options.IndentString = "    ";  
                    options.VerbatimOrder = true;  
                    options.BracingStyle = "C";  
  
                    using (StringWriter writer = new StringWriter(codeBuffer, CultureInfo.InvariantCulture))  
                    {  
                        codeDomProvider.GenerateCodeFromMember(documentField, writer, options);  
                        codeDomProvider.GenerateCodeFromMember(documentProperty, writer, options);  
                    }  
  
                }//end CoolDirective  
  
                //One directive processor can contain many directives.  
                //If you want to support more directives, the code goes here...  
                //-----------------------------------------------------------------  
                if (string.Compare(directiveName, "supercooldirective", StringComparison.OrdinalIgnoreCase) == 0)  
                {  
                    //code for SuperCoolDirective goes here...  
                }//end SuperCoolDirective  
  
                //Track how many times the processor has been called.  
                //-----------------------------------------------------------------  
                directiveCount++;  
  
            }//end ProcessDirective  
  
            public override void FinishProcessingRun()  
            {  
                this.codeDomProvider = null;  
  
                //important: do not do this:  
                //the get methods below are called after this method   
                //and the get methods can access this field  
                //-----------------------------------------------------------------  
                //this.codeBuffer = null;  
            }  
  
            public override string GetPreInitializationCodeForProcessingRun()  
            {  
                //Use this method to add code to the start of the   
                //Initialize() method of the generated transformation class.  
                //We do not need any pre-initialization, so we will just return "".  
                //-----------------------------------------------------------------  
                //GetPreInitializationCodeForProcessingRun runs before the   
                //Initialize() method of the base class.  
                //-----------------------------------------------------------------  
                return String.Empty;  
            }  
  
            public override string GetPostInitializationCodeForProcessingRun()  
            {  
                //Use this method to add code to the end of the   
                //Initialize() method of the generated transformation class.  
                //We do not need any post-initialization, so we will just return "".  
                //------------------------------------------------------------------  
                //GetPostInitializationCodeForProcessingRun runs after the  
                //Initialize() method of the base class.  
                //-----------------------------------------------------------------  
                return String.Empty;  
            }  
  
            public override string GetClassCodeForProcessingRun()  
            {  
                //Return the code to add to the generated transformation class.  
                //-----------------------------------------------------------------  
                return codeBuffer.ToString();  
            }  
  
            public override string[] GetReferencesForProcessingRun()  
            {  
                //This returns the references that we want to use when   
                //compiling the generated transformation class.  
                //-----------------------------------------------------------------  
                //We need a reference to this assembly to be able to call   
                //XmlReaderHelper.ReadXml from the generated transformation class.  
                //-----------------------------------------------------------------  
                return new string[]  
                {  
                    "System.Xml",  
                    this.GetType().Assembly.Location  
                };  
            }  
  
            public override string[] GetImportsForProcessingRun()  
            {  
                //This returns the imports or using statements that we want to   
                //add to the generated transformation class.  
                //-----------------------------------------------------------------  
                //We need CustomDP to be able to call XmlReaderHelper.ReadXml  
                //from the generated transformation class.  
                //-----------------------------------------------------------------  
                return new string[]  
                {  
                    "System.Xml",  
                    "CustomDP"  
                };  
            }  
        }//end class CustomDirectiveProcessor  
  
        //-------------------------------------------------------------------------  
        // the code that we are adding to the generated transformation class   
        // will call this method  
        //-------------------------------------------------------------------------  
        public static class XmlReaderHelper  
        {  
            public static XmlDocument ReadXml(string fileName)  
            {  
                XmlDocument d = new XmlDocument();  
  
                using (XmlTextReader reader = new XmlTextReader(fileName))  
                {  
                    try  
                    {  
                        d.Load(reader);  
                    }  
                    catch (System.Xml.XmlException e)  
                    {  
                        throw new DirectiveProcessorException("Unable to read the XML file.", e);  
                    }  
                }  
                return d;  
            }  
        }//end class XmlReaderHelper  
    }//end namespace CustomDP  
    ```  
  
    ```vb#  
    Imports System  
    Imports System.CodeDom  
    Imports System.CodeDom.Compiler  
    Imports System.Collections.Generic  
    Imports System.Globalization  
    Imports System.IO  
    Imports System.Text  
    Imports System.Xml  
    Imports System.Xml.Serialization  
    Imports Microsoft.VisualStudio.TextTemplating  
  
    Namespace CustomDP  
  
        Public Class CustomDirectiveProcessor  
        Inherits DirectiveProcessor  
  
            'this buffer stores the code that is added to the   
            'generated transformation class after all the processing is done   
            '---------------------------------------------------------------  
            Private codeBuffer As StringBuilder  
  
            'Using a Code Dom Provider creates code for the  
            'generated transformation class in either Visual Basic or C#.  
            'If you want your directive processor to support only one language, you  
            'can hard code the code you add to the generated transformation class.  
            'In that case, you do not need this field.  
            '--------------------------------------------------------------------------  
            Private codeDomProvider As CodeDomProvider  
  
            'this stores the full contents of the text template that is being processed  
            '--------------------------------------------------------------------------  
            Private templateContents As String  
  
            'These are the errors that occur during processing. The engine passes   
            'the errors to the host, and the host can decide how to display them,  
            'for example the the host can display the errors in the UI  
            'or write them to a file.  
            '---------------------------------------------------------------------  
            Private errorsValue As CompilerErrorCollection  
            Public Shadows ReadOnly Property Errors() As CompilerErrorCollection  
                Get  
                    Return errorsValue  
                End Get  
            End Property  
  
            'Each time this directive processor is called, it creates a new property.  
            'We count how many times we are called, and append "n" to each new  
            'property name. The property names are therefore unique.  
            '--------------------------------------------------------------------------  
            Private directiveCount As Integer = 0  
  
            Public Overrides Sub Initialize(ByVal host As ITextTemplatingEngineHost)  
  
                'we do not need to do any initialization work  
            End Sub  
  
            Public Overrides Sub StartProcessingRun(ByVal languageProvider As CodeDomProvider, ByVal templateContents As String, ByVal errors As CompilerErrorCollection)  
  
                'the engine has passed us the language of the text template  
                'we will use that language to generate code later  
                '----------------------------------------------------------  
                Me.codeDomProvider = languageProvider  
                Me.templateContents = templateContents  
                Me.errorsValue = errors  
  
                Me.codeBuffer = New StringBuilder()  
            End Sub  
  
            'Before calling the ProcessDirective method for a directive, the   
            'engine calls this function to see whether the directive is supported.  
            'Notice that one directive processor might support many directives.  
            '---------------------------------------------------------------------  
            Public Overrides Function IsDirectiveSupported(ByVal directiveName As String) As Boolean  
  
                If String.Compare(directiveName, "CoolDirective", StringComparison.OrdinalIgnoreCase) = 0 Then  
                    Return True  
                End If  
  
                If String.Compare(directiveName, "SuperCoolDirective", StringComparison.OrdinalIgnoreCase) = 0 Then  
                    Return True  
                End If  
  
                Return False  
            End Function  
  
            Public Overrides Sub ProcessDirective(ByVal directiveName As String, ByVal arguments As IDictionary(Of String, String))  
  
                If String.Compare(directiveName, "CoolDirective", StringComparison.OrdinalIgnoreCase) = 0 Then  
  
                    Dim fileName As String  
  
                    If Not (arguments.TryGetValue("FileName", fileName)) Then  
                        Throw New DirectiveProcessorException("Required argument 'FileName' not specified.")  
                    End If  
  
                    If String.IsNullOrEmpty(fileName) Then  
                        Throw New DirectiveProcessorException("Argument 'FileName' is null or empty.")  
                    End If  
  
                    'Now we add code to the generated transformation class.  
                    'This directive supports either Visual Basic or C#, so we must use the  
                    'System.CodeDom to create the code.  
                    'If a directive supports only one language, you can hard code the code.  
                    '--------------------------------------------------------------------------  
  
                    Dim documentField As CodeMemberField = New CodeMemberField()  
  
                    documentField.Name = "document" & directiveCount & "Value"  
                    documentField.Type = New CodeTypeReference(GetType(XmlDocument))  
                    documentField.Attributes = MemberAttributes.Private  
  
                    Dim documentProperty As CodeMemberProperty = New CodeMemberProperty()  
  
                    documentProperty.Name = "Document" & directiveCount  
                    documentProperty.Type = New CodeTypeReference(GetType(XmlDocument))  
                    documentProperty.Attributes = MemberAttributes.Public  
                    documentProperty.HasSet = False  
                    documentProperty.HasGet = True  
  
                    Dim fieldName As CodeExpression = New CodeFieldReferenceExpression(New CodeThisReferenceExpression(), documentField.Name)  
                    Dim booleanTest As CodeExpression = New CodeBinaryOperatorExpression(fieldName, CodeBinaryOperatorType.IdentityEquality, New CodePrimitiveExpression(Nothing))  
                    Dim rightSide As CodeExpression = New CodeMethodInvokeExpression(New CodeTypeReferenceExpression("XmlReaderHelper"), "ReadXml", New CodePrimitiveExpression(fileName))  
                    Dim thenSteps As CodeStatement() = New CodeStatement() {New CodeAssignStatement(fieldName, rightSide)}  
  
                    Dim ifThen As CodeConditionStatement = New CodeConditionStatement(booleanTest, thenSteps)  
                    documentProperty.GetStatements.Add(ifThen)  
  
                    Dim s As CodeStatement = New CodeMethodReturnStatement(fieldName)  
                    documentProperty.GetStatements.Add(s)  
  
                    Dim options As CodeGeneratorOptions = New CodeGeneratorOptions()  
                    options.BlankLinesBetweenMembers = True  
                    options.IndentString = "    "  
                    options.VerbatimOrder = True  
                    options.BracingStyle = "VB"  
  
                    Using writer As StringWriter = New StringWriter(codeBuffer, CultureInfo.InvariantCulture)  
  
                        codeDomProvider.GenerateCodeFromMember(documentField, writer, options)  
                        codeDomProvider.GenerateCodeFromMember(documentProperty, writer, options)  
                    End Using  
  
                End If  'CoolDirective  
  
                'One directive processor can contain many directives.  
                'If you want to support more directives, the code goes here...  
                '-----------------------------------------------------------------  
                If String.Compare(directiveName, "supercooldirective", StringComparison.OrdinalIgnoreCase) = 0 Then  
  
                    'code for SuperCoolDirective goes here  
                End If 'SuperCoolDirective  
  
                'Track how many times the processor has been called.  
                '-----------------------------------------------------------------  
                directiveCount += 1  
            End Sub 'ProcessDirective  
  
            Public Overrides Sub FinishProcessingRun()  
  
                Me.codeDomProvider = Nothing  
  
                'important: do not do this:  
                'the get methods below are called after this method   
                'and the get methods can access this field  
                '-----------------------------------------------------------------  
                'Me.codeBuffer = Nothing  
            End Sub  
  
            Public Overrides Function GetPreInitializationCodeForProcessingRun() As String  
  
                'Use this method to add code to the start of the   
                'Initialize() method of the generated transformation class.  
                'We do not need any pre-initialization, so we will just return "".  
                '-----------------------------------------------------------------  
                'GetPreInitializationCodeForProcessingRun runs before the   
                'Initialize() method of the base class.  
                '-----------------------------------------------------------------  
                Return String.Empty  
            End Function  
  
            Public Overrides Function GetPostInitializationCodeForProcessingRun() As String  
  
                'Use this method to add code to the end of the   
                'Initialize() method of the generated transformation class.  
                'We do not need any post-initialization, so we will just return "".  
                '------------------------------------------------------------------  
                'GetPostInitializationCodeForProcessingRun runs after the  
                'Initialize() method of the base class.  
                '-----------------------------------------------------------------  
                Return String.Empty  
            End Function  
  
            Public Overrides Function GetClassCodeForProcessingRun() As String  
  
                'Return the code to add to the generated transformation class.  
                '-----------------------------------------------------------------  
                Return codeBuffer.ToString()  
            End Function  
  
            Public Overrides Function GetReferencesForProcessingRun() As String()  
  
                'This returns the references that we want to use when   
                'compiling the generated transformation class.  
                '-----------------------------------------------------------------  
                'We need a reference to this assembly to be able to call   
                'XmlReaderHelper.ReadXml from the generated transformation class.  
                '-----------------------------------------------------------------  
                Return New String() {"System.Xml", Me.GetType().Assembly.Location}  
            End Function  
  
            Public Overrides Function GetImportsForProcessingRun() As String()  
  
                'This returns the imports or using statements that we want to   
                'add to the generated transformation class.  
                '-----------------------------------------------------------------  
                'We need CustomDP to be able to call XmlReaderHelper.ReadXml  
                'from the generated transformation class.  
                '-----------------------------------------------------------------  
                Return New String() {"System.Xml", "CustomDP"}  
            End Function  
        End Class 'CustomDirectiveProcessor  
  
        '--------------------------------------------------------------------------  
        ' the code that we are adding to the generated transformation class   
        ' will call this method  
        '--------------------------------------------------------------------------  
        Public Class XmlReaderHelper  
  
            Public Shared Function ReadXml(ByVal fileName As String) As XmlDocument  
  
                Dim d As XmlDocument = New XmlDocument()  
  
                Using reader As XmlTextReader = New XmlTextReader(fileName)  
  
                    Try  
                        d.Load(reader)  
  
                    Catch e As System.Xml.XmlException  
  
                        Throw New DirectiveProcessorException("Unable to read the XML file.", e)  
                    End Try  
                End Using  
  
                Return d  
            End Function  
        End Class 'XmlReaderHelper  
  
    End Namespace  
    ```  
  
4.  Pour [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] uniquement, ouvrez le **projet** menu, puis cliquez sur **propriétés de CustomDP**. Sur le **Application** sous l’onglet **espace de noms racine**, supprimez la valeur par défaut, `CustomDP`.  
  
5.  Sur le **fichier** menu, cliquez sur **Enregistrer tout**.  
  
6.  Dans le menu **Générer** , cliquez sur **Générer la solution**.  
  
### <a name="build-the-project"></a>Génération du projet  
 Générez le projet. Dans le menu **Générer** , cliquez sur **Générer la solution**.  
  
## <a name="registering-the-directive-processor"></a>Inscription du processeur de directive  
 Avant de pouvoir appeler une directive à partir d’un modèle de texte dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vous devez ajouter une clé de Registre pour le processeur de directive.  
  
> [!NOTE]
>  Si vous voulez installer le processeur de directive sur plusieurs ordinateurs, il est préférable de définir une extension [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] (VSIX) incluant un fichier .pkgdef avec votre assembly. Pour plus d’informations, consultez [déploiement d’un processeur de Directive personnalisé](../modeling/deploying-a-custom-directive-processor.md).  
  
 Des clés sont disponibles pour les processeurs de directive dans le Registre à l'emplacement suivant :  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\*.0\TextTemplating\DirectiveProcessors  
```  
  
 Pour les systèmes 64 bits, l'emplacement de Registre est :  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VisualStudio\*.0\TextTemplating\DirectiveProcessors  
```  
  
 Dans cette section, vous ajoutez au Registre une clé pour votre processeur de directive personnalisé, dans le même emplacement.  
  
> [!CAUTION]
>  Toute modification incorrecte du Registre peut gravement endommager votre système. Avant d'apporter des modifications au Registre, sauvegardez toutes les données utiles qui se trouvent sur l'ordinateur.  
  
#### <a name="to-add-a-registry-key-for-the-directive-processor"></a>Pour ajouter une clé de Registre pour le processeur de directive  
  
1.  Exécuter le `regedit` en utilisant le menu Démarrer ou la ligne de commande.  
  
2.  Accédez à l’emplacement **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\\*.0\TextTemplating\DirectiveProcessors**, puis cliquez sur le nœud.  
  
     Sur les systèmes 64 bits, utilisez **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VisualStudio\\\*.0\TextTemplating\DirectiveProcessors**  
  
3.  Ajoutez une nouvelle clé nommée CustomDirectiveProcessor.  
  
    > [!NOTE]
    >  Il s'agit du nom que vous utiliserez dans le champ Processeur de vos directives personnalisées. Ce nom ne doit pas nécessairement correspondre au nom de la directive, au nom de la classe du processeur de directive ou à l'espace de noms du processeur de directive.  
  
4.  Ajoutez une nouvelle valeur de chaîne nommée Class ayant la valeur CustomDP.CustomDirectiveProcessor pour le nom de la nouvelle chaîne.  
  
5.  Ajoutez une nouvelle valeur de chaîne nommée CodeBase ayant une valeur égale au chemin d’accès du fichier CustomDP.dll que vous avez créé précédemment dans cette procédure pas à pas.  
  
     Par exemple, le chemin d’accès peut se présenter comme `C:\UserFiles\CustomDP\bin\Debug\CustomDP.dll`.  
  
     Votre clé de Registre doit avoir les valeurs suivantes :  
  
    |Nom|Type|Données|  
    |----------|----------|----------|  
    |(Default)|REG_SZ|(valeur non définie)|  
    |Classe|REG_SZ|CustomDP.CustomDirectiveProcessor|  
    |CodeBase|REG_SZ|**\<Chemin d’accès à votre Solution >**CustomDP\bin\Debug\CustomDP.dll|  
  
     Si vous avez placé l'assembly dans le GAC, les valeurs doivent se présenter comme suit :  
  
    |Nom|Type|Données|  
    |----------|----------|----------|  
    |(Default)|REG_SZ|(valeur non définie)|  
    |Classe|REG_SZ|CustomDP.CustomDirectiveProcessor|  
    |Assembly|REG_SZ|CustomDP.dll|  
  
6.  Redémarrez Visual Studio.  
  
## <a name="testing-the-directive-processor"></a>Test du processeur de directive  
 Pour tester le processeur de directive, vous devez écrire un modèle de texte qui l'appelle.  
  
 Dans cet exemple, le modèle de texte appelle la directive et passe le nom d'un fichier XML qui contient la documentation d'un fichier de classe.
  
 Le modèle de texte utilise ensuite le <xref:System.Xml.XmlDocument>propriété que la directive crée pour naviguer dans le code XML et imprimer les commentaires de documentation.</xref:System.Xml.XmlDocument>  
  
#### <a name="to-create-an-xml-file-for-use-in-testing-the-directive-processor"></a>Pour créer un fichier XML à utiliser pour le test du processeur de directive  
  
1.  Créez un fichier texte nommé `DocFile.xml` à l’aide de n’importe quel éditeur de texte (par exemple, le bloc-notes).  
  
    > [!NOTE]
    >  Vous pouvez créer ce fichier dans n'importe quel emplacement (par exemple, C:\Test\DocFile.xml).  
  
2.  Ajoutez le code suivant au fichier texte :  
  
    ```  
    <?xml version="1.0"?>  
    <doc>  
        <assembly>  
            <name>xmlsample</name>  
        </assembly>  
        <members>  
            <member name="T:SomeClass">  
                <summary>Class level summary documentation goes here.</summary>  
                <remarks>Longer comments can be associated with a type or member through the remarks tag</remarks>  
            </member>  
            <member name="F:SomeClass.m_Name">  
                <summary>Store for the name property</summary>  
            </member>   
            <member name="M:SomeClass.#ctor">  
                <summary>The class constructor.</summary>   
            </member>  
            <member name="M:SomeClass.SomeMethod(System.String)">  
                <summary>Description for SomeMethod.</summary>  
                <param name="s">Parameter description for s goes here</param>  
                <seealso cref="T:System.String">You can use the cref attribute on any tag to reference a type or member and the compiler will check that the reference exists.</seealso>  
            </member>  
            <member name="M:SomeClass.SomeOtherMethod">  
                <summary>Some other method.</summary>  
                <returns>Return results are described through the returns tag.</returns>  
                <seealso cref="M:SomeClass.SomeMethod(System.String)">Notice the use of the cref attribute to reference a specific method</seealso>  
            </member>  
            <member name="M:SomeClass.Main(System.String[])">  
                <summary>The entry point for the application.</summary>  
                <param name="args">A list of command line arguments</param>  
            </member>  
            <member name="P:SomeClass.Name">  
                <summary>Name property</summary>  
                <value>A value tag is used to describe the property value</value>  
            </member>  
        </members>  
    </doc>  
    ```  
  
3.  Enregistrez et fermez le fichier.  
  
#### <a name="to-create-a-text-template-to-test-the-directive-processor"></a>Pour créer un modèle de texte de façon à tester le processeur de directive  
  
1.  Dans Visual Studio, créez un projet de bibliothèque de classes C# ou Visual Basic nommé TemplateTest.  
  
2.  Ajoutez un nouveau fichier modèle de texte nommé TestDP.tt.  
  
3.  Assurez-vous que le **un outil personnalisé** propriété de TestDP.tt a la valeur `TextTemplatingFileGenerator`.  
  
4.  Remplacez le contenu de TestDP.tt par le texte suivant.  
  
    > [!NOTE]
    >  Veillez à remplacer la chaîne `YOUR PATH>` avec le chemin d’accès au fichier DocFile.xml.  
  
     Le langage du modèle de texte ne doit pas nécessairement correspondre à celui du processeur de directive.  
  
    ```c#  
    <#@ assembly name="System.Xml" #>  
    <#@ template debug="true" #>  
    <#@ output extension=".txt" #>  
  
    <#  //This will call the custom directive processor. #>  
    <#@ CoolDirective Processor="CustomDirectiveProcessor" FileName="<YOUR PATH>\DocFile.xml" #>  
  
    <#  //Uncomment this line if you want to see the generated transformation class. #>  
    <#  //System.Diagnostics.Debugger.Break(); #>  
  
    <#  //This will use the results of the directive processor. #>  
    <#  //The directive processor has read the XML and stored it in Document0. #>  
    <#  
        XmlNode node = Document0.DocumentElement.SelectSingleNode("members");  
  
        foreach (XmlNode member in node.ChildNodes)  
        {  
            XmlNode name = member.Attributes.GetNamedItem("name");  
            WriteLine("{0,7}:  {1}", "Name", name.Value);  
  
            foreach (XmlNode comment in member.ChildNodes)  
            {  
                WriteLine("{0,7}:  {1}", comment.Name, comment.InnerText);  
            }  
            WriteLine("");  
        }  
    #>  
  
    <#  //You can call the directive processor again and pass it a different file. #>  
    <# //@ CoolDirective Processor="CustomDirectiveProcessor" FileName="<YOUR PATH>\<Your Second File>" #>  
  
    <#  //To use the results of the second directive call, use Document1. #>  
    <#  
        //XmlNode node2 = Document1.DocumentElement.SelectSingleNode("members");  
  
        //...  
    #>  
    ```  
  
    ```vb#  
    <#@ assembly name="System.Xml" #>  
    <#@ template debug="true" language="vb" #>  
    <#@ output extension=".txt" #>  
  
    <#  'This will call the custom directive processor. #>  
    <#@ CoolDirective Processor="CustomDirectiveProcessor" FileName="<YOUR PATH>\DocFile.xml" #>  
  
    <#  'Uncomment this line if you want to see the generated transformation class. #>  
    <#  'System.Diagnostics.Debugger.Break() #>  
  
    <#  'This will use the results of the directive processor. #>  
    <#  'The directive processor has read the XML and stored it in Document0. #>  
    <#  
        Dim node as XmlNode = Document0.DocumentElement.SelectSingleNode("members")  
  
        Dim member As XmlNode  
        For Each member In node.ChildNodes  
  
            Dim name As XmlNode = member.Attributes.GetNamedItem("name")  
            WriteLine("{0,7}:  {1}", "Name", name.Value)  
  
            Dim comment As XmlNode  
            For Each comment In member.ChildNodes  
                WriteLine("{0,7}:  {1}", comment.Name, comment.InnerText)  
            Next  
  
            WriteLine("")  
        Next  
    #>  
  
    <#  'You can call the directive processor again and pass it a different file. #>  
    <# '@ CoolDirective Processor="CustomDirectiveProcessor" FileName="<YOUR PATH>\DocFileTwo.xml" #>  
  
    <#  'To use the results of the second directive call, use Document1. #>  
    <#  
        'node = Document1.DocumentElement.SelectSingleNode("members")  
  
        '...  
    #>  
    ```  
  
    > [!NOTE]
    >  Dans cet exemple, la valeur du paramètre `Processor` est `CustomDirectiveProcessor`. La valeur du paramètre `Processor` doit correspondre au nom de la clé de Registre du processeur.  
  
5.  Sur le **fichier** menu, cliquez sur **Enregistrer tout**.  
  
#### <a name="to-test-the-directive-processor"></a>Pour tester le processeur de directive  
  
1.  Dans **l’Explorateur de solutions**, droit sur TestDP.tt, puis **exécuter un outil personnalisé**.  
  
     Pour [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] les utilisateurs, TestDP.txt n’apparaisse pas dans **l’Explorateur de solutions** par défaut. Pour afficher tous les fichiers assignés au projet, ouvrez le **projet** menu et cliquez sur **afficher tous les fichiers**.  
  
2.  Dans **l’Explorateur de solutions**, développez le nœud TestDP.txt, puis double-cliquez sur le fichier TestDP.txt pour l’ouvrir dans l’éditeur.  
  
     La sortie de texte générée s'affiche. La sortie doit se présenter comme suit :  
  
    ```  
       Name:  T:SomeClass  
    summary:  Class level summary documentation goes here.  
    remarks:  Longer comments can be associated with a type or member through the remarks tag  
  
       Name:  F:SomeClass.m_Name  
    summary:  Store for the name property  
  
       Name:  M:SomeClass.#ctor  
    summary:  The class constructor.  
  
       Name:  M:SomeClass.SomeMethod(System.String)  
    summary:  Description for SomeMethod.  
      param:  Parameter description for s goes here  
    seealso:  You can use the cref attribute on any tag to reference a type or member and the compiler will check that the reference exists.  
  
       Name:  M:SomeClass.SomeOtherMethod  
    summary:  Some other method.  
    returns:  Return results are described through the returns tag.  
    seealso:  Notice the use of the cref attribute to reference a specific method  
  
       Name:  M:SomeClass.Main(System.String[])  
    summary:  The entry point for the application.  
      param:  A list of command line arguments  
  
       Name:  P:SomeClass.Name  
    summary:  Name property  
      value:  A value tag is used to describe the property value  
    ```  
  
## <a name="adding-html-to-generated-text"></a>Ajout de code HTML au texte généré  
 Après avoir testé votre processeur de directive personnalisé, vous pouvez ajouter du code HTML au texte généré.  
  
#### <a name="to-add-html-to-the-generated-text"></a>Pour ajouter du code HTML au texte généré  
  
1.  Remplacez le code figurant dans TestDP.txt par le code suivant : Le code HTML est mis en surbrillance. Veillez à remplacer la chaîne `YOUR PATH` avec le chemin d’accès au fichier DocFile.xml.  
  
    > [!NOTE]
    >  Ouvrez supplémentaire \<# et fermantes #> balises séparent le code des instructions des balises HTML.  
  
    ```c#  
    <#@ assembly name="System.Xml" #>  
    <#@ template debug="true" #>  
    <#@ output extension=".htm" #>  
  
    <#  //this will call the custom directive processor #>  
    <#@ CoolDirective Processor="CustomDirectiveProcessor" FileName="<YOUR PATH>\DocFile.xml" #>  
  
    <#  //uncomment this line if you want to see the generated transformation class #>  
    <#  //System.Diagnostics.Debugger.Break(); #>  
  
    <html><body>  
  
    <#  //this will use the results of the directive processor #>  
    <#  //the directive processor has read the XML and stored it in Document0#>  
    <#  
        XmlNode node = Document0.DocumentElement.SelectSingleNode("members");  
  
        foreach (XmlNode member in node.ChildNodes)  
        {  
    #>  
    <h3>  
    <#      
            XmlNode name = member.Attributes.GetNamedItem("name");  
            WriteLine("{0,7}:  {1}", "Name", name.Value);  
    #>  
    </h3>  
    <#  
            foreach (XmlNode comment in member.ChildNodes)  
            {  
                WriteLine("{0,7}:  {1}", comment.Name, comment.InnerText);  
    #>  
    <br/>  
    <#  
            }  
        }  
    #>  
    </body></html>  
    ```  
  
    ```vb#  
    <#@ assembly name="System.Xml" #>  
    <#@ template debug="true" language="vb" #>  
    <#@ output extension=".htm" #>  
  
    <#  'this will call the custom directive processor #>  
    <#@ CoolDirective Processor="CustomDirectiveProcessor" FileName="<YOUR PATH>\DocFile.xml" #>  
  
    <#  'uncomment this line if you want to see the generated transformation class #>  
    <#  'System.Diagnostics.Debugger.Break() #>  
  
    <html><body>  
  
    <#  'this will use the results of the directive processor #>  
    <#  'the directive processor has read the XML and stored it in Document0#>  
    <#  
        Dim node as XmlNode = Document0.DocumentElement.SelectSingleNode("members")  
  
        Dim member As XmlNode  
        For Each member In node.ChildNodes  
    #>  
    <h3>  
    <#      
            Dim name As XmlNode = member.Attributes.GetNamedItem("name")  
            WriteLine("{0,7}:  {1}", "Name", name.Value)  
    #>  
    </h3>  
    <#  
            Dim comment As XmlNode  
            For Each comment In member.ChildNodes  
                WriteLine("{0,7}:  {1}", comment.Name, comment.InnerText)  
    #>  
    <br/>  
    <#  
            Next  
        Next  
    #>  
    </body></html>  
    ```  
  
2.  Sur le **fichier** menu, cliquez sur **Enregistrer TestDP.txt**.  
  
3.  Pour afficher la sortie dans un navigateur, dans **l’Explorateur de solutions**, droit sur TestDP.htm, puis cliquez sur **afficher dans le navigateur**.  
  
     Votre sortie doit être identique au texte d'origine, à cette différence près que le format HTML doit lui être appliqué. Chaque nom d'élément doit s'afficher en gras.

