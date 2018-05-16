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

## Body 
```kotlin
fun panelBody() =
        document.create.div {
            classes=setOf("panel-body")
            form {
                classes=setOf("form-horizontal")
                role="form"
                formGroupName()
                formGroupEmail()
                formGroupPass()
                formGroupRePass()
                formGroupControlGenre()
                formGroupControlCountry()
                formControlAddress()
                formControlLegal()
            }
        }


private fun FORM.formControlLegal() =
        div {
            classes= setOf("form-group form-check")
            div {
                classes= setOf("form-check")
                input {
                    classes= setOf("form-check-input")
                    type=InputType.checkBox
                }
                label {
                    classes= setOf("form-check-label")
                    htmlFor="gridCheck"
                    +" Acepto los términos y condiciones"
                }
            }
        }

private fun FORM.formControlAddress() =
        div{
            classes=setOf("form-group")
            label {
                classes=setOf("col-sm-2 control-label")
                htmlFor="Address"
                +"Dirección"
            }
            div {
                classes = setOf("col-sm-10")
                textArea {
                    classes = setOf("form-control")
                    name=""
                    cols=""
                    rows=""
                }
            }
        }

private fun FORM.formGroupControlCountry() =
        div{
            classes=setOf("form-group")
            label {
                classes=setOf("col-sm-2 control-label")
                htmlFor="State"
                +"País"
            }
            div {
                classes = setOf("col-sm-10")
                select {
                    classes = setOf("form-control")
                    option { +"España" }
                    option { +"Francia" }
                    option { +"Italia" }
                    option { +"Otros" }
                }
            }
        }

private fun FORM.formGroupControlGenre() =
        div {
            classes = setOf("form-group")
            label {
                classes = setOf("col-sm-2 control-label")
                htmlFor = "genero"
                +"Género"
            }
            div {
                classes = setOf("col-sm-10")
                div {
                    classes = setOf("radio-inline")
                    div {
                        classes=setOf("form-check form-check-inline")
                        input {
                            classes=setOf("form-check-input")
                            id = "radiobutton1"
                            name = "sampleradiobutton"
                            value = ""
                            type = InputType.radio
                        }
                        label {
                            classes=setOf("form-check-label")
                            +"Masculino  "
                        }
                    }

                    div {
                        classes=setOf("form-check form-check-inline")
                        input {
                            classes=setOf("form-check-input")
                            id = "radiobutton2"
                            name = "sampleradiobutton"
                            value = ""
                            type = InputType.radio
                        }
                        label {
                            classes=setOf("form-check-label")
                            +"Femenino  "
                        }
                    }
                }
            }
        }


private fun FORM.formGroupRePass() =
        div{
            classes=setOf("form-group")
            label {
                classes=setOf("col-sm-2 control-label")
                htmlFor="password"
                +"Confirmar Password"
            }
            div {
                classes=setOf("col-sm-10")
                input {
                    type = InputType.password
                    classes=setOf("form-control")
                    id="confirmpass"
                }
            }
        }

private fun FORM.formGroupPass() =
        div{
            classes=setOf("form-group")
            label {
                classes=setOf("col-sm-2 control-label")
                htmlFor="password"
                +"Password"
            }
            div {
                classes=setOf("col-sm-10")
                input {
                    type = InputType.password
                    classes=setOf("form-control")
                    id="pass"
                }
            }
        }

private fun FORM.formGroupEmail() {
    div {
        classes = setOf("form-group")
        label {
            classes = setOf("col-sm-2 control-label")
            htmlFor = "gmail"
            +"Gmail "
        }
        div {
            classes = setOf("col-sm-10")
            div {
                classes = setOf("mb-2")
                div {
                    classes = setOf("input-group-prepend")
                    div {
                        classes = setOf("input-group-text")
                        +"@"
                    }
                    input {
                        classes = setOf("form-control")
                        type = InputType.text
                        id = "inlineFormInputGroup"
                    }
                }
            }

        }

    }
}

private fun FORM.formGroupName() {
    div {
        classes = setOf("panel-body")
        label {
            classes = setOf("col-sm-2 control-label")
            htmlFor = "name"
            +"Nombre "
        }
        div {
            classes = setOf("col-sm-10")
            input {
                classes = setOf("form-control")
                type = InputType.email
                id = "_email"
            }
        }

    }
}
```

## Footer
```kotlin
fun panelFoorter()=
        document.create.div {
            classes = setOf("panel-footer")
            style = "overflow:hidden;text-align:right;"
            buttonGroup()
        }

private fun DIV.buttonGroup() {
    div {
        classes = setOf("form-group")
        colButton()
    }
}

private fun DIV.colButton() {
    div {
        classes = setOf("col-sm-offset-2 col-sm-10")
        button {
            type = ButtonType.submit
            classes = setOf("btn btn-success btn-sm")
            attributes["data-toggle"] = "modal"
            attributes["data-target"] = "#Modal"
            +"Enviar"
        }
    }
}

```

## Header 
```kotlin
fun panelHeader() =
        document.create.div {
            classes = setOf("panel-heading")
            h3 {
                classes = setOf("panel-title text-center")
                +"Formulario w/ Kotlin JS - vicboma1"
            }
}
```

## ShowModal
```kotlin
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
