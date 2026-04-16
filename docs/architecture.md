## Robot class diagram

```mermaid
classDiagram
class CRobot {
  +setup()
  +loop()
}

class CMotorControl {
  +setSpeed()
  +stop()
}

class CGrabber {
  +grab()
  +release()
  +move()
}

CRobot --> CMotorControl

CRobot --> CGrabber