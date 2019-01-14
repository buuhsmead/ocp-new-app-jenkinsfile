#!groovy

println "Hello"
println "Only purpose is to show how to start a Pipeline in OCP"

openshift.withCluster() {
    openshift.withProject() {
          /** Selectors are a core concept in the DSL. They allow the user to invoke operations **/
    /** on group of objects which satisfy a given criteria. **/

    // Create a Selector capable of selecting all service accounts in mycluster's default project
    def saSelector = openshift.selector( 'serviceaccount' )

    // Prints `oc describe serviceaccount` to Jenkins console
    saSelector.describe()

    // Selectors also allow you to easily iterate through all objects they currently select.
    saSelector.withEach { // The closure body will be executed once for each selected object.
        // The 'it' variable will be bound to a Selector which selects a single
        // object which is the focus of the iteration.
        echo "Service account: ${it.name()} is defined in ${openshift.project()}"
    }

    // Prints a list of current service accounts to the console
    echo "There are ${saSelector.count()} service accounts in project ${openshift.project()}"
    echo "They are named: ${saSelector.names()}"

    }
}
