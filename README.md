# kafkainstall

#To track install steps for AMQ streams
504  oc login https://master.kasriniv-8dab.openshiftworkshop.com:443 --token=R-WUkT0EKtkgWuMonD43iR6d51tVQLt9WAG2XrROkJ4
  505  oc new-project myproject
  506  pwd
  507  cd ~/Documents/Customers/Experian/kafkainstall/
  508  oc apply -f ./install_and_examples/install/cluster-operator -n myproject
  509  oc apply -f ./install_and_examples/examples/templates/cluster-operator/ -n myproject
  510  oc apply -f ./install_and_examples/examples/kafka/kafka-ephemeral.yaml 
  511  oc apply -f install_and_examples/examples/kafka-connect/kafka-connect.yaml 
  512  oc run kafka-producer -ti --image=registry.access.redhat.com/amqstreams-1/amqstreams10-kafka-openshift:1.0.0 --rm=true --restart=Never -- bin/kafka-console-producer.sh --broker-list my-cluster-kafka-bootstrap:9092 --topic my-topic
  513  oc run kafka-consumer -ti --image=registry.access.redhat.com/amqstreams-1/amqstreams10-kafka-openshift:1.0.0 --rm=true --restart=Never -- bin/kafka-console-consumer.sh --bootstrap-server my-cluster-kafka-bootstrap:9092 --topic my-topic --from-beginning
  
  #all done adding