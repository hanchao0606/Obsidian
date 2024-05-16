```java 
package com.testEnum;  
public enum Status {  
    ONE(1) {  
        @Override  
        public boolean canChangeTo(Status newStatus) {  
            return newStatus == ONE || newStatus == TWO;  
        }  
    },  
    TWO(2) {  
        @Override  
        public boolean canChangeTo(Status newStatus) {  
            return newStatus == TWO || newStatus == THREE;  
        }  
    },  
    THREE(3) {  
        @Override  
        public boolean canChangeTo(Status newStatus) {  
            return newStatus == THREE || newStatus == FOUR;  
        }  
    },  
    FOUR(4) {  
        @Override  
        public boolean canChangeTo(Status newStatus) {  
            return newStatus == FOUR;  
        }  
    };  
  
    private final int value;  
  
    Status(int value) {  
        this.value = value;  
    }  
  
    public int getValue() {  
        return value;  
    }  
  
    public static Status fromValue(int value) {  
        for (Status status : Status.values()) {  
            if (status.getValue() == value) {  
                return status;  
            }  
        }  
        throw new IllegalArgumentException("Invalid value: " + value);  
    }  
  
    public abstract boolean canChangeTo(Status newStatus);  
}


int frontendStatus = 1;  
Status status = Status.fromValue(frontendStatus);  
Status dataBaseStatus = Status.ONE;  
boolean canChange = dataBaseStatus.canChangeTo(status);  
System.out.println("args = " + canChange);
```