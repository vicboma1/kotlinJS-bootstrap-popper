# Bootstrap + Kotlin JS (DSL)

## Scritps 
  * Kotlin
  * Kotlin JS
  * Kotlinx html 0.6.10
  * Bootstrap 4.1.1
  * Popper 1.14.0
  * Jquery 3.3.1

## Style sheet
* Bootstrap 4.1.1
* Bootstrap Theme 3.3.7
 

## Form
![](https://raw.githubusercontent.com/vicboma1/kotlinJS-bootstrap-popper/master/assets/jsForm.gif)

## Main

```kotlin
fun main(args: Array<String>) {
    document.apply {
        getElementById("header")?.appendChild(panelHeader())
        getElementById("body")?.apply {
            appendChild(panelBody())
            appendChild(panelFoorter())
            appendChild(showDialog())
        }
    }
}
```


## ShowModal
```kotlin

package bootStrap

import kotlinx.html.*
import kotlinx.html.dom.create
import kotlinx.html.js.div
import kotlin.browser.document

fun showDialog() =
        document.create.div {
            classes= setOf("modal fade")
            id="Modal"
            attributes["tabindex"] ="-1"
            role ="dialog"
            attributes["aria-labelledby"] ="exampleModalLabel"
            attributes["aria-hidden"]="true"
            dialogModal()
        }

private fun DIV.dialogModal() {
    div {
        classes = setOf("modal-dialog")
        role = "document"
        containerModal()
    }
}

private fun DIV.containerModal() {
    div {
        classes = setOf("modal-content")
        headerModal()
        bodyModal()
        footerModal()
    }
}

private fun DIV.headerModal() {
    div {
        classes = setOf("modal-header")
        h5 {
            classes = setOf("modal-title")
            id = "exampleModalLabel"
            +"Solicitud realizada con éxito"
        }
        button {
            type = ButtonType.button
            classes = setOf("close")
            attributes["data-dismiss"] = "modal"
            attributes["aria-label"] = "Close"
            span {
                attributes["aria-hidden"] = "true"
                +"x"
            }
        }
    }
}

private fun DIV.bodyModal() {
    div {
        classes = setOf("modal-body")
        +"Su formulario se ha rellenado correctamente "
    }
}

private fun DIV.footerModal() {
    div {
        classes = setOf("modal-footer")
        button {
            type = ButtonType.button
            classes = setOf("btn btn-secondary")
            attributes["data-dismiss"] = "modal"
            +"Aceptar"
        }
        span { }
        button {
            type = ButtonType.button
            classes = setOf("btn btn-primary")
            attributes["data-dismiss"] = "modal"
            +"Cancelar"
        }
    }
}
```



## Html
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">

    <title>Kotlin JavaScript - BootStrap Formulario</title>

    <link rel="stylesheet"
          href="https://stackpath.bootstrapcdn.com/bootstrap/4.1.0/css/bootstrap.min.css"
          integrity="sha384-9gVQ4dYFwwWSjIDZnLEWnxCjeSWFphJiwGPXr1jddIhOegiu1FwO5qRGvFXOdJZ4"
          crossorigin="anonymous">

    <link rel="stylesheet"
          href="//maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap-theme.min.css"
          integrity="sha384-rHyoN1iRsVXV4nD0JutlnGaslCJuC7uwjduW9SVrLvRYooPp2bWYgmgJQIXwl/Sp"
          crossorigin="anonymous">

</head>
<body>

<div class="container-fluid">
        <div class="card">
            <div class="card-header" id="header"> </div>
            <div class="card-body" id="body"> </div>
        </div>
</div>

    <script src="lib/kotlin.js" ></script>
    <script src="lib/kotlinx-html-js.js" ></script>

    <script src="https://code.jquery.com/jquery-3.3.1.slim.min.js"
            integrity="sha384-q8i/X+965DzO0rT7abK41JStQIAqVgRVzpbzo5smXKp4YfRvH+8abtTE1Pi6jizo"
            crossorigin="anonymous"></script>


    <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.0/umd/popper.min.js"
            integrity="sha384-cs/chFZiN24E4KMATLdqdvsezGxaGsi4hLGOzlXwp5UZB1LY//20VyM2taTB4QvJ"
            crossorigin="anonymous"></script>

    <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.1.0/js/bootstrap.min.js"
            integrity="sha384-uefMccjFJAIv6A+rW+L4AHf99KvxDjWSu1z9VI8SKNVmz4sk7buKt/6v9KI65qnm"
            crossorigin="anonymous"></script>

    <script src="05-bootstrapDSL.js" ></script>

</body>
</html>
```


@Author : Victor Bolinches

@vicboma1
